# Embedded-System-For-Linux
Embedded System For Linux
1.移植了sim900a的程序 
2.修改了部分注释，但是还有一部分没有修改
3.生成的目标文件之后 当前目录会有子目录中的.o  修改了makfile  添加了rm -rf *.o 删除了当前的所有*.o文件
4.在makefile中的clean目标中添加了移除当前文件*.o的操作，每次编译完成之后只会剩下赶紧的可执行文件
5.修改了子目录和当前目录的makefile中工具链的宏定义，在arm-linux-编译器编译通过。



1.串口接收采用规定好的通信格式进行接收，具体的通信格式如下
*串口数据通信格式:	帧头(两个字节:0xaa,0x55) + 帧类型(一个字节，保留字段，暂时不添加) + 
*					长度(一个字节) + 数据 + 帧尾(两个字节:0xff,0xff)
*					(不添加校验，长度只包含数据位个数)
*例如:	0xaa 0x55	0x00	0x02 	0x01 0x02 	0xff 0xff
*说明: 数据通信格式是为了解决串口接收数据不完整的情况，对于串口数据的发送暂时不考虑
*		现在只用到了帧头	长度	数据 	帧尾

2.修改了调试打印的信息,能够将接收到的字符按照字符串进行输出(目前只能接收16进制格式的数据，不能够接收上位机发送过来的字符串)




1.移植了dht11驱动程序，并且测试通过
2.修改了文件的分类，创建了内核模块专用的文件夹
3.dht11应用程序编写完成，可以进行简单的读取(没有涉及到滤波，现在是原始数据输出)