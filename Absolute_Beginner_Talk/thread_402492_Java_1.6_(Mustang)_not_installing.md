---
title: "Java 1.6 (Mustang) not installing"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2007-04-05
I followed the instructions on digg.com as shown:  > [INDENT] deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) dapper 3v1n0
#deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) dapper 3v1n0
[/INDENT]Now continue:[INDENT]sudo apt-get update
sudo apt-get install  make-jpkg-mustang
sudo make-jpkg-mustang[/INDENT][INDENT]
And got:


> Do you want to install the sun-java6-jre_1.6.0_02-ea-b01_i386.deb now?
 [Y/n]: y(Reading database ... 112890 files and directories currently installed.)
Preparing to replace sun-java6-jre 1.6.0_02-ea-b01 (using .../sun-java6-jre_1.6.0_02-ea-b01_i386.deb) ...
Unpacking replacement sun-java6-jre ...
Setting up sun-java6-jre (1.6.0_02-ea-b01) ...


You can always check your java version using "update-alternatives" and "java -version"

Script made by Trevi&#65533;o <http://3v1n0.tuxfamily.org/blog>
Suggestions, bugs and so on... [EMAIL="trevi55@gmail.com"]trevi55@gmail.com[/EMAIL]
*****@*****-desktop:~$ java -version
**java version "1.5.0_06"**
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM **(build 1.5.0_06-b05,** mixed mode, sharing)

Any thoughts on this ?

Edit: It says it's replacing the same version because I had tried this method already, and it looks like it THINKS that 1.6 is installed, but it's not ?
[/INDENT]

---

### Post by adam.tropics on 2007-04-06
In a terminal try

```
sudo update-alternatives --config java
```You will I suspect find it is installed, and just need to tell it to use the newer version.

---

