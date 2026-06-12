---
title: "Limwire problems"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Linuxgenius on 2007-06-17
i seem i cant get limewire or frostwire to work is there a special way to go about this?  there should be a sticky around here isnt it? this is what i see in my desktop[ATTACH]35708[/ATTACH]

 can some1 help me

---

### Post by Daremo on 2007-06-17
Do you have java installed? Both limewire and frostwire require java runtime enviornment (JRE) - the real java, not the open source clone (gij it's called if I remember correctly). You can check easily by opening a terminal window and type: java -version

you should see results such as:

java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

Cheers!

---

### Post by Clay_Banger on 2007-06-17
your problem is a java problem, many people have come across it before(just search the forums), including me. I simply installed the java from the repos and updated the default java (sudo update-alternatives java) and it worked.

---

### Post by Linuxgenius on 2007-06-17
ok i did it and this is what i got[ATTACH]35717[/ATTACH]

---

### Post by Clay_Banger on 2007-06-17
> **Linuxgenius said:**
> ok i did it and this is what i got[ATTACH]35717[/ATTACH]
oops :-?
this is what you want:
```
sudo update-alternatives --config java
```

---

### Post by Linuxgenius on 2007-06-17
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 1
Using `/usr/bin/gij-wrapper-4.1' to provide `java'.
linuxgenius@linuxgenius-laptop:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/bin/gij-wrapper-4.1
 +        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 1
Using `/usr/bin/gij-wrapper-4.1' to provide `java'.


now limewire wont start

---

### Post by Clay_Banger on 2007-06-17
try:
```
sudo aptitude install sun-java-jre
```
then use:
```
sudo update-alternatives --config java
```
to select the one that you just added

---

### Post by Linuxgenius on 2007-06-17
linuxgenius@linuxgenius-laptop:~$ sudo aptitude install sun-java-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "sun-java-jre"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
linuxgenius@linuxgenius-laptop:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/bin/gij-wrapper-4.1
 +        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 


took me back to where i was at right?

---

### Post by Clay_Banger on 2007-06-17
grr, im an idiot
```
sudo aptitude install sun-java6-jre
```
is what u want

---

### Post by Linuxgenius on 2007-06-18
linuxgenius@linuxgenius-laptop:~$ sudo aptitude install sun-java6-jre
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done


any other ideas?

---

### Post by ThinkBuntu on 2007-06-18
By the way, you want Frostwire and not Limewire. Limewire will constantly hit you up for money and actually limit your download performance and search results (presumably to get you to buy their Pro edition). Frostwire also has a .deb package you can download, which means no need for alien to convert the RPM.

---

### Post by Linuxgenius on 2007-06-18
how do i remove limewire and get frostwire?

---

### Post by qamelian on 2007-06-18
You can download frostwire from : [http://www.frostwire.com/](http://www.frostwire.com/)

Also, you seem to be using Beryl. There is a known issue with displaying java apps in Beryl with Sun 1.6 JRE. You need  to either turn off beryl when using this app or download and install manually the latest JRE (1.6u1) from Sun Microsystems. Some Java apps will still not display properly, but most will.

---

### Post by mark. on 2007-06-18
i also have the same problem, i have java 1.6 running and get that white screen of nothing when it starts.

i got my frostwire from the frostwire site (the linux version.)

---

### Post by Linuxgenius on 2007-06-18
ok installed it and still nothing

---

### Post by sibot on 2007-06-18
It is a problem, I faced in linux too. Anyway, when I'm back to XP, due to some ubuntu incompatibility reasons. I installed the latest version of Java for windows, and LimeWire didnt seem to work on it. So I installed an earlier version of Java, and limewire was working. I think LimeWire has some compatibility issues with the latest Java Env.

---

### Post by Linuxgenius on 2007-06-18
so install a oldersion of java??? where do i get it from and how do i get it?

---

### Post by Clay_Banger on 2007-06-18
the version of java that i am running that works with frostwire and beryl is from here:
[http://java.sun.com/javase/downloads/index.jsp]("http://java.sun.com/javase/downloads/index.jsp")

"JDK 6u1" is what you want
click download > accept license agreement > "Linux self-extracting file "
download the file to the desktop
once the file has finished downloading open up the terminal
```
cd ~/
chmod +x jdk-6u1-linux-i586.bin
sudo ./jdk-6u1-linux-i586.bin
```
then use:
```
sudo update-alternatives --config java
```
and select the newly added option

---

### Post by Linuxgenius on 2007-06-19
linuxgenius@linuxgenius-laptop:~$ cd ~/
linuxgenius@linuxgenius-laptop:~$ chmod +x jdk-6u1-linux-i586.bin
chmod: cannot access `jdk-6u1-linux-i586.bin': No such file or directory
linuxgenius@linuxgenius-laptop:~$ sudo ./jdk-6u1-linux-i586.bin
Password:
sudo: ./jdk-6u1-linux-i586.bin: command not found
linuxgenius@linuxgenius-laptop:~$

---

### Post by defrex on 2007-06-19
Do you use Beryl, by chance? Check this out:

[https://help.ubuntu.com/community/LimeWire](https://help.ubuntu.com/community/LimeWire)

---

### Post by thefoolisme on 2007-06-19
It didn't install it again because it's installed already.  I copied this from your previous post:  

There are 2 alternatives which provide `java'.

Selection Alternative
-----------------------------------------------
* 1 /usr/bin/gij-wrapper-4.1
+ 2 /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:

Did you select "2" or just hit enter?  You needed to select the Java 6 option.

---

### Post by Linuxgenius on 2007-06-19
limewire is in my apps but when i click it nothin happeneds

---

### Post by defrex on 2007-06-19
Turn off beryl and then try.

---

### Post by Linuxgenius on 2007-06-19
how do u turn beryl off?

---

### Post by Linuxgenius on 2007-06-19
??bump

---

### Post by uthturn on 2007-06-19
right click on the gem and goto select window manager and select metacity i'm having the same problem as you and i just did it and limewire works now can anybody provide a fix for this beryl and java problem

---

### Post by mark. on 2007-06-20
^yeah it finally worked xDD

i tried changing to metacity and then opening frostwire, and then changing to beryl again. seems to work, but kinda laggy :/

---

### Post by Linuxgenius on 2007-06-23
i just did a clean install with ubuntu

---

### Post by SnakeHips on 2007-06-24
I'm having the same prob with frostwire. From console it's telling me the jave/jre cant be found...

pete@myplace:~$ frostwire
Starting FrostWire...
Java exec not found in PATH, starting auto-search...
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
pete@myplace:~$ 

....however .its installed here....

/usr/lib/jvm/java-6-sun-1.6.0.00/jre

So....how do I tell the program where to find it ?

---

