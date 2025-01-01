## 1.什么是静态变量/成员变量/局部变量？有何性质？
+ **静态变量** 是用static 关键字声明的变量，静态变量在类加载时初始化，且在类的所有实例之间共享。可以通过类名直接访问.
+ **成员变量**是声明在类中，描述类的属性的变量，只能通过对象访问。
+ **局部变量**是声明在方法、构造函数或块中的变量，其作用域仅限于声明它的方法、构造函数或块
##  2.什么是overload和override？有什么区别？
+ overload指重载，在同一个类中定义多个方法，它们具有相同的名称但不同的参数列表（参数类型、参数数量不同）。
+ override指重写，子类重新定义父类中已有的方法，方法名称、参数列表和返回类型必须完全相同
## 3.public、protected、default、private 成员变量的访问权限 
| 访问修饰符 | 类内部 | 同一个包 | 子类 | 其他包 |
|------------|--------|----------|------|--------|
| `public`   | ✔️     | ✔️       | ✔️   | ✔️     |
| `protected`| ✔️     | ✔️       | ✔️   | ❌     |
| `default`  | ✔️     | ✔️       | ❌   | ❌     |
| `private`  | ✔️     | ❌       | ❌   | ❌     |
## 4.在异常处理的过程中，try，catch和finally各有什么作用。 
| **块**     | **作用**                                                                 |
|------------|------------------------------------------------------------------------|
| **try**    | 定义可能抛出异常的代码块，监控异常。                                         |
| **catch**  | 捕获并处理 **try** 块中抛出的异常。                                         |
| **finally**| 定义无论是否发生异常都必须执行的代码，通常用于清理操作。                         |
## 5.什么是继承/封装/多态？
+ **继承**：子类继承父类的属性和方法，建立类之间的层次关系，子类可以扩展或重写父类的功能
+ **封装**：封装是将数据（属性）和操作数据的方法（行为）捆绑在一起，并隐藏内部实现细节，只暴露必要的接口。
+ **多态**：*多态是指同一个方法或操作在不同对象中具有不同的行为。它允许使用父类类型的引用调用子类的方法*。
## 6.请解释this/super关键字的使用方法。 
this 引用当前对象，super 引用父类对象，分别用于访问当前类和父类的成员及构造函数
## 7.说明抽象类和接口有什么区别。
+ **抽象类**用 abstract 声明，可以包含抽象方法和具体方法，抽象类通过 extends 继承，子类必须实现抽象方法（除非子类也是抽象类）
+ **接口**用 interface 声明，通过 implements 实现，类必须实现所有抽象方法，接口支持多继承，一个类可以实现多个接口，接口成员变量类型默认是 public static final，成员方法默认是public abstract
## 8.final 关键字的作用。
+ final 修饰的变量是常量，值不能改变。
+ final 修饰的方法不能被子类重写。
+ final 修饰的类不能被继承。
## 9.实现多线程的方法。
+ **继承Thread类**，重写run()方法，调用start()方法启动线程。
+ **实现Runnable接口**，重写run()方法，**创建Thread对象**，调用start()方法启动线程。
## 10. 列举 Java 中常用的字节输入流和字节输出流并说明其特点，至少 3 对。
 1. **FileInputStream 和 FileOutputStream**
- **特点**：
  - **FileInputStream**：用于从文件中读取字节数据。
  - **FileOutputStream**：用于将字节数据写入文件。
  - **用途**：适用于文件读写操作，处理二进制数据（如图片、音频等）。
2. **BufferedInputStream 和 BufferedOutputStream**
- **特点**：
  - **BufferedInputStream**：在 `InputStream` 基础上**添加缓冲区**，提高读取效率。
  - **BufferedOutputStream**：在 `OutputStream` 基础上**添加缓冲区**，提高写入效率。
  - **用途**：适用于需要高效读写数据的场景，减少频繁的 I/O 操作。
3. **DataInputStream 和 DataOutputStream**
- **特点**：
  - **DataInputStream**：可以从输入流中读取**基本数据类型**（如 `int`、`double` 等）。
  - **DataOutputStream**：可以向输出流中写入基本数据类型。
  - **用途**：适用于读写基本数据类型的场景，如网络通信或文件存储。
## 11.多线程中 start 方法和 run 方法分别有什么作用？
+ start：创建新线程，线程进入就绪状态，自动调用 run 方法启动线程
+ run：定义线程任务，直接调用不会启动新线程。
## 12.简述Java中的异常处理机制的简单原理和应用。 
+ Java 的异常处理机制通过 try-catch-finally 结构来捕获和处理程序运行时可能发生的错误，当 try 块中的代码抛出异常时，程序会立即停止执行 try 块中剩余的代码，程序查找匹配的 catch 块来处理异常，无论是否发生异常，finally 块中的代码都会被执行
+ 使用 try-catch 块捕获并处理异常，通过继承 Exception 或 RuntimeException 创建自定义异常，在方法头中使用 throws 声明可能抛出的异常，将异常传递给调用者处理
## 13.简述throw和throws关键字的区别。
+ throw用于在方法体中手动抛出一个异常，生成异常对象的过程，声明在方法体内
+ throws用于在方法头中声明一个可能抛出的异常，并将其抛给调用者处理
## 14.简述静态方法与非静态方法的区别？
| 特性         | 静态方法                         | 非静态方法                       |
|--------------|----------------------------------|----------------------------------|
| **定义**     | 用 `static` 修饰，属于类          | 不用 `static` 修饰，属于对象      |
| **调用方式** | 通过类名调用                     | 通过对象调用                     |
| **访问权限** | 只能访问静态成员                 | 可以访问静态和非静态成员          |
| **生命周期** | 与类相同                         | 与对象相同                       |
| **使用场景** | 不依赖对象状态的操作             | 依赖对象状态的操作               |
## 15.什么是构造方法？构造方法有哪些特点？
+ 构造方法是一种**特殊的实例方法**，它用来**创建和初始化对象**
+ 方法名与类名相同，没有返回类型，支持重载，不能继承，如果未定义构造方法，Java 会提供默认的无参构造方法
## 16.什么叫类中类？主要包括哪几种类中类？请简述其特点和作用。
类中类是指在一个类的内部定义的类
| 类型             | 特点                                                                 | 作用                                   |
|------------------|--------------------------------------------------------------------|--------------------------------------|
| **静态嵌套类**   | 不依赖外部类实例，不能直接访问外部类非静态成员                         | 逻辑上属于外部类但不依赖实例的场景         |
| **非静态嵌套类** | 依赖外部类实例，可以直接访问外部类所有成员                             | 与外部类紧密相关的场景，封装实现细节         |
| **局部类**       | 作用域限于方法或代码块，只能访问 `final` 或等效于 `final` 的局部变量     | 仅在方法内部使用的场景，简化代码             |
| **匿名类**       | 没有名字，一次性使用，只能访问 `final` 或等效于 `final` 的局部变量       | 简化代码，用于事件处理或回调函数             |
## 17.简述静态代码块/构造代码块/同步代码块/普通代码块的特点。
| 类型             | 特点                                                                 | 作用                                   |
|------------------|--------------------------------------------------------------------|--------------------------------------|
| **静态代码块**   | 用 static 关键字修饰的代码块，类加载时执行，**只执行一次**                                             | 初始化静态变量或加载静态资源             |
| **构造代码块**   | 在类中直接定义的代码块，没有修饰符。**每次创建对象时执行，优先于构造方法**                                     | 初始化实例变量或执行通用操作             |
| **同步代码块**   | 用**synchronized** 关键字修饰的代码块。实现线程同步，确保同一时间只有一个线程执行                               | 多线程环境下保护共享资源                 |
| **普通代码块**   | 在方法或语句中定义的代码块。限定变量作用域，控制变量生命周期                                       | 组织代码，减少变量作用域                 |
## 18.简述实现字节流/字符流的读写过程。
| 类型     | 读过程                                      | 写过程                                      |
|----------|-------------------------------------------|-------------------------------------------|
| **字节流** | 创建字节输入流（如 FileInputStream） → 使用 read() 方法读取字节数据 → 处理数据 → 关闭流 | 创建字节输出流（如 FileoutputStream）→ 使用 write() 方法写入字节数据 → 关闭流       |
| **字符流** | 创建字符输入流（如 FileReader 或 BufferedReader）→ 使用 read() 方法读取字符数据 → 处理数据 → 关闭流 | 创建字符输出流（如 FileWriter 或 BufferedWriter） → 使用 write() 方法写入字符数据 → 关闭流       |
## 19.什么叫向上转型/向下转型？
| 特性         | 向上转型（Upcasting）                     | 向下转型（Downcasting）                   |
|--------------|------------------------------------------|------------------------------------------|
| **定义**     | 子类对象赋值给父类引用                    | 父类引用转换为子类引用                    |
| **转换方式** | 自动进行                                 | 需要强制转换                              |
| **访问权限** | 只能访问父类成员，**多态调用子类重写的方法**    | 可以访问子类特有的成员                    |
| **使用场景** | 实现多态，简化代码设计                    | 访问子类特有的成员                        |
## 20.什么叫泛型？
允许在定义类、接口或方法时使用使用占位符（类型参数）来表示数据类型，而不是使用具体的类型。

## 1.定义一个抽象类Shape，包含抽象方法getArea()，Shape类派生出Rectangle矩形类，Rectangle 类派生出Cube类。
```go
// 抽象类 Shape
abstract class Shape {
    // 抽象方法 getArea
    public abstract double getArea();
}

// Rectangle 类继承自 Shape
class Rectangle extends Shape {
    private double length;
    private double width;

    // 构造函数
    public Rectangle(double length, double width) {
        this.length = length;
        this.width = width;
    }

    // 实现 getArea 方法
    public double getArea() {
        return length * width;
    }
}

// Cube 类继承自 Rectangle
class Cube extends Rectangle {
    private double height;

    // 构造函数
    public Cube(double length, double width, double height) {
        super(length, width);
        this.height = height;
    }

    // 重写 getArea 方法，计算立方体的表面积
    public double getArea() {
        return 2 * (super.getArea() + (super.getArea() / length) * height + (super.getArea() / width) * height);
    }
}
public class Main {
    public static void main(String[] args) {
        Rectangle rectangle = new Rectangle(5, 10);
        System.out.println("Rectangle Area: " + rectangle.getArea());

        Cube cube = new Cube(5, 10, 15);
        System.out.println("Cube Surface Area: " + cube.getArea());
    }
}
```
## 2.一个数如果恰好等于它的因子之和，这个数就称为 "完数"。例如 6=1＋2＋3。编程找出1000以内的所有完数。
```go
public class PerfectNumbers {
    public static void main(String[] args) {
        for (int i = 1; i <= 1000; i++) {
            if (isPerfectNumber(i)) {
                System.out.println(i + " 是一个完数");
            }
        }
    }

    // 判断一个数是否是完数
    public static boolean isPerfectNumber(int number) {
        int sum = 0;
        for (int i = 1; i <= number / 2; i++) {
            if (number % i == 0) {
                sum += i;
            }
        }
        return sum == number;
    }
}
```
## 3.已知：Math.random();返回 0-1 之间的 double 数。编写程序段，定义一个含有数字 1到100整数数组（数组长度为100），然后将其随机打乱。
```go
public class ShuffleArray {
    public static void main(String[] args) {
        // 定义包含数字 1 到 100 的数组
        int[] array = new int[100];
        for (int i = 0; i < array.length; i++) {
            array[i] = i + 1;
        }

        // 利用 Math.random() 随机打乱数组
        for (int i = 0; i < array.length; i++) {
            int randomIndex = (int) (Math.random() * array.length); // 生成随机索引
            int temp = array[i]; // 交换当前元素与随机索引处的元素
            array[i] = array[randomIndex];
            array[randomIndex] = temp;
        }

        // 输出打乱后的数组
        for (int num : array) {
            System.out.print(num + " ");
        }
    }
}
```
## 4.编写一个函数，能够将传入的字符串按字母逆序打印。
```go
public class ReverseString {
    public static void main(String[] args) {
        String input = "Hello, World!";
        printReverse(input);
    }

    // 按字母逆序打印字符串
    public static void printReverse(String str) {
        for (int i = str.length() - 1; i >= 0; i--) {
            System.out.print(str.charAt(i));
        }
    }
}
```
## 5.应用 FileInputStream 类，编写程序从磁盘读取一个文件（文件路径为：c:/test/A.java），并将文件内容显示在屏幕上。 
```go
import java.io.FileInputStream;
import java.io.IOException;

public class ReadFile {
    public static void main(String[] args) {
        String filePath = "c:/test/A.java"; // 文件路径

        try (FileInputStream fis = new FileInputStream(filePath)) 
        {
            int content;
            // 逐个字节读取文件内容并显示
            while ((content = fis.read()) != -1) {
                System.out.print((char) content);
            }
        } catch (IOException e) {
            System.out.println("读取文件时出错: " + e.getMessage());
        }
    }
}
```
## 6.打印机有黑白打印机和彩色打印机，不同类型的打印机打印效果不同。请根据小题要求编写打印机类，用多态实现打印机的功能。 
## （1）编写一个打印机的抽象类，在该类中定义一个打印的抽象方法。 
## （2）分别编写彩色打印机和黑白打印机的非抽象类，继承打印机抽象类。 
## （3）编写一个测试类，测试彩色打印机类和黑白打印机类是否正常。 
```go
abstract class Printer {
    // 定义打印的抽象方法
    public abstract void print();
}
// 彩色打印机类
class ColorPrinter extends Printer {
    @Override
    public void print() {
        System.out.println("彩色打印机：打印彩色文档");
    }
}

// 黑白打印机类
class BlackWhitePrinter extends Printer {
    @Override
    public void print() {
        System.out.println("黑白打印机：打印黑白文档");
    }
}
public class PrinterTest {
    public static void main(String[] args) {
        // 使用多态创建打印机对象
        Printer colorPrinter = new ColorPrinter();
        Printer blackWhitePrinter = new BlackWhitePrinter();

        // 测试打印功能
        colorPrinter.print();        // 输出：彩色打印机：打印彩色文档
        blackWhitePrinter.print();   // 输出：黑白打印机：打印黑白文档
    }
}
```
## 7.某本书中有100万个汉字，请统计每个汉字的使用次数。如何实现？写出相关流程。
```go
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;
import java.util.HashMap;

public class CharacterCount {
    public static void main(String[] args) {
        String filePath = "book.txt"; // 文件路径
        HashMap<Character, Integer> charCountMap = new HashMap<>();

        try (BufferedReader reader = new BufferedReader(new FileReader(filePath))) {
            int ch;
            // 逐个字符读取文件
            while ((ch = reader.read()) != -1) {
                char character = (char) ch;
                // 判断是否为汉字
                if (isChineseCharacter(character)) {
                    // 更新汉字计数
                    charCountMap.put(character, charCountMap.getOrDefault(character, 0) + 1);
                }
            }
        } catch (IOException e) {
            System.out.println("读取文件时出错: " + e.getMessage());
        }

        // 输出每个汉字及其出现次数
        for (HashMap.Entry<Character, Integer> entry : charCountMap.entrySet()) {
            System.out.println("汉字: " + entry.getKey() + ", 出现次数: " + entry.getValue());
        }
    }

    // 判断字符是否为汉字
    private static boolean isChineseCharacter(char character) {
        return character >= 0x4E00 && character <= 0x9FA5; // 汉字 Unicode 范围
    }
}
```
## 8.两个羽毛球队进行比赛，各出三人。甲队为a, b, c三人，乙队为x, y, z三人。已抽签决定比赛名单。有人向队员打听比赛的名单。a说他不和x比，c说他不和x, z比，请编程序找出三队赛手的名单。
```go
public class MatchScheduler {
    public static void main(String[] args) {
        char[] teamA = {'a', 'b', 'c'}; // 甲队
        char[] teamB = {'x', 'y', 'z'}; // 乙队

        // 遍历所有可能的对阵组合
        for (char a : teamB) {
            for (char b : teamB) {
                for (char c : teamB) {
                    // 检查对阵是否满足条件
                    if (a != b && a != c && b != c && a != 'x' && c != 'x' && c != 'z') {
                        System.out.println("a vs " + a);
                        System.out.println("b vs " + b);
                        System.out.println("c vs " + c);
                    }
                }
            }
        }
    }
}
```
## 9.编写程序统计一个字符串中大写字母的个数。 
```go
public class CountUppercase {
    public static void main(String[] args) {
        String str = "Hello World! Java Programming.";
        int count = 0;

        // 遍历字符串中的每个字符
        for (int i = 0; i < str.length(); i++) {
            if (Character.isUpperCase(str.charAt(i))) {
                count++;
            }
        }

        System.out.println("大写字母的个数: " + count);
    }
}
```
## 10.编写一个简单的加密程序，要求对于接收到的原始的明文字母序列，将其中的每个字母都置换为字母表中其后的第5个字母，然后输出。
```go
public class SimpleEncryption {
    public static void main(String[] args) {
        String plaintext = "Hello World!"; // 明文字符串
        String ciphertext = encrypt(plaintext, 5); // 加密
        System.out.println("加密后的密文: " + ciphertext);
    }

    // 加密方法
    public static String encrypt(String plaintext, int shift) {
        StringBuilder ciphertext = new StringBuilder();

        for (int i = 0; i < plaintext.length(); i++) {
            char ch = plaintext.charAt(i);
            // 处理大写字母
            if (Character.isUpperCase(ch)) {
                ch = (char) ((ch - 'A' + shift) % 26 + 'A');
            }
            // 处理小写字母
            else if (Character.isLowerCase(ch)) {
                ch = (char) ((ch - 'a' + shift) % 26 + 'a');
            }
            // 非字母字符保持不变
            ciphertext.append(ch);
        }

        return ciphertext.toString();
    }
}
```
## 11.编写程序，从键盘读取用户输入两个字符串，并重载 3 个函数分别实现这两个字符串的拼接、整数相加和浮点数相加。要进行异常处理，对输入的不符合要求的字符串提示给用户，不能使程序崩溃。
```go
import java.util.Scanner;

public class StringOperations {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // 读取用户输入的两个字符串
        System.out.print("请输入第一个字符串: ");
        String str1 = scanner.nextLine();
        System.out.print("请输入第二个字符串: ");
        String str2 = scanner.nextLine();

        // 调用重载函数并处理异常
        try {
            System.out.println("字符串拼接结果: " + add(str1, str2));
        } catch (Exception e) {
            System.out.println("字符串拼接时发生错误: " + e.getMessage());
        }

        try {
            System.out.println("整数相加结果: " + add(Integer.parseInt(str1), Integer.parseInt(str2)));
        } catch (NumberFormatException e) {
            System.out.println("输入的不是有效的整数，无法进行整数相加。");
        }

        try {
            System.out.println("浮点数相加结果: " + add(Double.parseDouble(str1), Double.parseDouble(str2)));
        } catch (NumberFormatException e) {
            System.out.println("输入的不是有效的浮点数，无法进行浮点数相加。");
        }

        //scanner.close();
    }

    // 字符串拼接
    public static String add(String str1, String str2) {
        return str1 + str2;
    }

    // 整数相加
    public static int add(int num1, int num2) {
        return num1 + num2;
    }

    // 浮点数相加
    public static double add(double num1, double num2) {
        return num1 + num2;
    }
}
```
## 12.请按如下要求编写代码： 
①请定义一个名为Card 的扑克牌类，该类有两个private 访问权限的字符串变量 face
和 suit：分别描述一张牌的牌面值（如：A、K、Q、J、10、9、…、3、2 等）和花色（如：
“黑桃”、“红桃”、“梅花”和“方块”）。 
②定义Card类中的public访问权限的构造方法，为类中的变量赋值； 
③定义protected 访问权限的方法getFace()，得到扑克牌的牌面值;  
④定义protected 访问权限的方法getSuit()，得到扑克牌的花色;  
⑤主类中的main方法中创建一张牌（红桃A）的对象，输出这张牌的花色和牌面值。 
```go
public class Card {
    // 定义 private 访问权限的变量
    private String face; // 牌面值
    private String suit; // 花色

    // ② 定义 public 访问权限的构造方法
    public Card(String face, String suit) {
        this.face = face;
        this.suit = suit;
    }

    // ③ 定义 protected 访问权限的 getFace() 方法
    protected String getFace() {
        return face;
    }

    // ④ 定义 protected 访问权限的 getSuit() 方法
    protected String getSuit() {
        return suit;
    }
}
public class Main {
    public static void main(String[] args) {
        // 创建一张牌（红桃A）的对象
        Card card = new Card("A", "红桃");

        // 输出这张牌的花色和牌面值
        System.out.println("花色: " + card.getSuit() + ", 牌面值: " + card.getFace());
    }
}
```
## 13.编程计算字符串中给定子串的出现次数
```go
public class SubstringCount {
    public static void main(String[] args) {
        String str = "Java is a powerful programming language. Java is widely used.";
        String substring = "Java";

        // 计算子串出现次数
        int count = countSubstring(str, substring);
        System.out.println("子串 \"" + substring + "\" 出现的次数: " + count);
    }

    // 计算子串出现次数的方法
    public static int countSubstring(String str, String substring) {
        int count = 0;
        int index = 0;

        // 使用 indexOf 方法查找子串
        while ((index = str.indexOf(substring, index)) != -1) {
            count++;
            index += substring.length(); // 移动索引位置
        }

        return count;
    }
}
```
## 14.假设存在一个文本文件（numbers.txt），其中仅包含数字，数字之间用空格或换行符分隔。文件内容示例如下所示： 
1  2  3  4  5  6  7  8  9 
5  6  7  8  9  0  1    
9  5  0  
... ... 
请编写一个 JAVA 程序，实现读取指定文件（numbers.txt）的内容，并将文件中所有的
数字相加后输出。请注意异常处理，例如文件不存在或文件内容格式不正确等情况。
```go
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class SumNumbersFromFile {
    public static void main(String[] args) {
        String filePath = "numbers.txt"; // 文件路径
        int sum = 0;

        try (Scanner scanner = new Scanner(new File(filePath))) {
            // 逐行读取文件内容
            while (scanner.hasNextLine()) {
                String line = scanner.nextLine();
                // 按空格分割每行的数字
                String[] numbers = line.split("\\s+");
                for (String number : numbers) {
                    try {
                        // 将字符串转换为整数并累加
                        sum += Integer.parseInt(number);
                    } catch (NumberFormatException e) {
                        System.out.println("文件内容格式不正确，无法解析数字: " + number);
                    }
                }
            }
            System.out.println("文件中所有数字的和为: " + sum);
        } catch (FileNotFoundException e) {
            System.out.println("文件不存在，请检查文件路径: " + filePath);
        }
    }
}
```
## 15.给定两个二进制字符串 x 和 y ，编写一个函数，以二进制字符串的形式返回它们的和。示例：如果: x = “111”, y = “1”，则输出: “1000”
```go
public class BinaryAddition {
    public static void main(String[] args) {
        String x = "111";
        String y = "1";
        System.out.println(addBinary(x, y)); // 输出: 1000
    }

    public static String addBinary(String x, String y) {
        StringBuilder result = new StringBuilder();
        int i = x.length() - 1, j = y.length() - 1;
        int carry = 0;

        // 从右到左逐位相加
        while (i >= 0 || j >= 0 || carry > 0) {
            int sum = carry;
            if (i >= 0) {
                sum += x.charAt(i) - '0'; // 将字符转换为数字
                i--;
            }
            if (j >= 0) {
                sum += y.charAt(j) - '0'; // 将字符转换为数字
                j--;
            }
            result.append(sum % 2); // 当前位的值
            carry = sum / 2; // 进位
        }

        // 反转结果字符串
        return result.reverse().toString();
    }
}
```
## 16. 一个文本文件，其中包含了若干个英文字符串，请构造一个类，并通过其中的若干个方法实现如下功能： 
（1）打开并读取该文本文件，将其中所有的英文字符串读取出来并存储到二维数组中，其
中二维数组的每一行用于依序存储一个字符串； 
（2）统计该文本文件包含的单词总数； 
（3）统计给定单词出现的次数； 
（4）将给定的英文单词替换成为指定的单词，同时对源文件进行刷新；  
（5）把用户从键盘输入的字符串追加到该文本文件的末尾。
```go
import java.io.*;
import java.util.Scanner;

public class TextFileProcessor {
    private String[][] strings; // 存储字符串的二维数组
    private String filePath; // 文件路径

    // 构造方法，初始化文件路径
    public TextFileProcessor(String filePath) {
        this.filePath = filePath;
    }

    // （1）读取文件并将字符串存储到二维数组中
    public void readFileToArray() throws IOException {
        BufferedReader reader = new BufferedReader(new FileReader(filePath));
        String line;
        int rowCount = 0;

        // 计算文件行数
        while (reader.readLine() != null) {
            rowCount++;
        }
        reader.close();

        // 初始化二维数组
        strings = new String[rowCount][];
        reader = new BufferedReader(new FileReader(filePath));

        // 逐行读取文件并存储到二维数组
        for (int i = 0; i < rowCount; i++) {
            line = reader.readLine();
            strings[i] = line.split(" ");
        }
        reader.close();
    }

    // （2）统计单词总数
    public int countTotalWords() {
        int count = 0;
        for (String[] row : strings) {
            count += row.length;
        }
        return count;
    }

    // （3）统计给定单词出现的次数
    public int countWordOccurrences(String word) {
        int count = 0;
        for (String[] row : strings) {
            for (String str : row) {
                if (str.equals(word)) {
                    count++;
                }
            }
        }
        return count;
    }

    // （4）将给定单词替换为指定单词，并刷新源文件
    public void replaceWordInFile(String oldWord, String newWord) throws IOException {
        BufferedReader reader = new BufferedReader(new FileReader(filePath));
        StringBuilder content = new StringBuilder();
        String line;

        // 读取文件内容并替换单词
        while ((line = reader.readLine()) != null) {
            line = line.replaceAll("\\b" + oldWord + "\\b", newWord);
            content.append(line).append("\n");
        }
        reader.close();

        // 将替换后的内容写回文件
        BufferedWriter writer = new BufferedWriter(new FileWriter(filePath));
        writer.write(content.toString());
        writer.close();
    }

    // （5）将用户输入的字符串追加到文件末尾
    public void appendToFile(String input) throws IOException {
        BufferedWriter writer = new BufferedWriter(new FileWriter(filePath, true));
        writer.write("\n" + input);
        writer.close();
    }

    // 主方法，测试功能
    public static void main(String[] args) {
        try {
            TextFileProcessor processor = new TextFileProcessor("textfile.txt");

            // （1）读取文件并存储到二维数组
            processor.readFileToArray();

            // （2）统计单词总数
            System.out.println("单词总数: " + processor.countTotalWords());

            // （3）统计给定单词出现的次数
            String word = "hello";
            System.out.println("单词 \"" + word + "\" 出现的次数: " + processor.countWordOccurrences(word));

            // （4）替换单词并刷新文件
            processor.replaceWordInFile("hello", "hi");

            // （5）将用户输入的字符串追加到文件末尾
            Scanner scanner = new Scanner(System.in);
            System.out.print("请输入要追加的字符串: ");
            String input = scanner.nextLine();
            processor.appendToFile(input);
            scanner.close();

        } catch (IOException e) {
            System.out.println("文件操作出错: " + e.getMessage());
        }
    }
}
```