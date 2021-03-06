## OOP特性
![](./笔记and笔记图片/oop.webp)

## 开始学习C++
1. **插入运算符(<<)**：输出是从程序流出的一系列字符，<<可以将右侧的信息插入到流中
2. **名称空间**：不同的名称空间内可以容纳同名函数
    ```c++
    Microflop::wanda();
    Piscine::wanda();         //不同函数
    /******************************************************************************/
    using namespace std;      //包含在名称空间std内的函数均可使用
    using std::cut;           // 使iostream内的cont可以使用
    ```
3. 所有iostream对象都是字符流
4. **类定义描述的是数据格式及其用法，而对象则是根据数据格式规范创建的实体**

## 复合类型
1. **函数拼接**
    ```c++
    cin.get(name).get()
    ```
2. **String类**
   ```c++
   string str1.str2;        //声明变量
   cin>>str1;
   str2+=str1;              //用+把另一个对象（或字符串）加到末尾
3. **共用体**:变量可以存储int、long、double，条件是再不同时间进行；即，只能同时存在一种共用体内包含的元素类型
    ```c++
    union one4all
    {
        int int_val;
        long long_val;
        double double_val;
    }
    ```
4. **枚举**：
    - 枚举量是整型，可被提升为int型，但int类型不能自动转换为枚举类型（但可以强制转换）
    - 枚举只定义了赋值运算符
    - 可以显示定义枚举量的值，第一个元素默认为0，后面没初始化的比前面的大1
    - 可以用枚举来定义switch语句中使用的符号产量
    ```c++
    enum spectrum {red = 2, orange = 4, yellow = 6, blue = 8};  //spectrum为枚举变量，只有3个值
    spectrum band;
    band = red;
    band = bits(6);             //通过强制转换可以将枚举取值范围内的任何整数值赋给枚举变量
    ```
    - 枚举范围的确定:
    $2^{n_1}>枚举量最大值,2^{n_2}<枚举量最小值$  
    $枚举范围为[2^{n_1}-1,2^{n_2}-1](如果为负则+1)$
5. **指针**
    - 一定要在对指针进行解引用之前，将指针初始化为一个确定的、适当的地址

## 类
1. 类是一种将抽象转换为用户定义类型的C++工具，它将数据表示和操纵数据的方法组合成一个整洁的包
    - 用户定义类型指的是实现抽象接口的类设计
2. 访问控制（数据隐藏）：
    - 类分为公有部分和私有部分
    - 数据项通常放在私有部分，组成类接口的成员函数放在共有部分
    - 静态成员由所有对象共享，需要static共有函数修改（不能用const）
    - 使用类的对象访问共有部分，通过类的对象（类接口）访问类的数据成员
3. 初始化：
    - 调用公共接口
    - 使用构造函数 Classname Name(data)
    - 成员初始化列表语法
4. 友元：
    - 友元函数不是成员函数，但它与成员函数的访问权限相同
    - 函数定义不用加类名，friend关键字
    - 可以显示使用2个对象
5. 共有继承：
    - 在基类描述的*共有特征*上增加新的特征，由此派生出另一个类
    - 派生类继承了基类的实现、接口
    - 派生类需要自己的构造函数，可以根据需要添加额外的数据成员和成员函数
    - 基类的指针可以指向基类的对象，也可以指向派生类的对象
    - virtual关键字
        - 函数将根据引用或指针指向的对象的类型来选择方法
        - virtual关键字只用于类声明的方法原型中
        - 如果要在派生类中重新定义基类的方法，通常应将基类方法声明为虚的
    - protected关键字
        -在类外，protected成员与private成员相似；在派生类中，protected成员与public成员相似
    - explicit关键字
        - 防止类构造函数的隐式自动转换
6. 抽象基类（ABC理念）：
    - 从要派生的类中抽象出相同的特性，将这些特性放到一个类中，然后从这个类进行派生
    - 至少使用一个*纯虚接口*
        - 纯虚函数提供未实现的函数，声明的结尾处=0
        - 即表明同一个特性，但在不同派生类中实现方法不同
7. 私有继承：
    - 只获得实现，不包含接口
    - 与包含相比，子对象没有名称，需要使用类名来表示构造函数
        