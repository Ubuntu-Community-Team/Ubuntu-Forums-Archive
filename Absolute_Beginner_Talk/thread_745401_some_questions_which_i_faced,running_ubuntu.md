---
title: "some questions which i faced,running ubuntu"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by pinaki nag on 2008-04-04
hello friends, i am very new in linux.i have just installed ubuntu 7.10 today...i was using 
windows for a long time.now this totally new platform is really alien to me,so i need some help 
from u people.my questions are....
1.i have a broadband connection of BSNL 900 plus.it provides an adsl modem which i used to connect in 
usb port,and it work fine,now what will be the case for ubuntu??it is asking for some usb drivers to be installed.
which i cant understand.

2.i program in java,while in case of windows i hv to install jdk,and then do some path settings....now the source code is to be written in notepad
and then compliled from CMD promt.what will be the case in linux?any IDE can i use for this purpose?

3.i also do sql in oracle XE edition,is there any diff distribution for linux?..

---

### Post by Inxsible on 2008-04-04
2) You can use the same IDE's that you use in Windows. Eclipse and Netbeans both have linux versions. You can also use any other IDE's that you may like, Scite comes to mind.

---

### Post by TheLions on 2008-04-04
> **pinaki nag said:**
> 
2.i program in java,while in case of windows i hv to install jdk,and then do some path settings....now the source code is to be written in notepad
and then compliled from CMD promt.what will be the case in linux?any IDE can i use for this purpose?


2 for IDE you could use Kdevelop, Anjutra and Eclipse. Also you can compile your code from terminal if you want.

1 and 3 I dunno

---

### Post by prshah on 2008-04-04
> **pinaki nag said:**
> 
1.i have a broadband connection of BSNL 900 plus.it provides an adsl modem which i used to connect in 
usb port,and it work fine,now what will be the case for ubuntu??it is asking for some usb drivers to be installed.
which i cant understand.

2.i program in java,while in case of windows i hv to install jdk,and then do some path settings....now the source code is to be written in notepad
and then compliled from CMD promt.what will be the case in linux?any IDE can i use for this purpose?

3.i also do sql in oracle XE edition,is there any diff distribution for linux?..

1) Most likely the adsl router (modem) will ALSO have an ethernet connection. You can ask BSNL the changeover procedure or post here for more information on how to change over. If it doesn't have an additional ethernet port, you can ask BSNL to replace it with a ADSL ethernet router or buy one from the open market for about Rs. 1000~1500.

2) Java approach is same in linux; only you will use gedit instead of notepad and terminal instead of cmd. You do not need to manually make path settings, just install using ```
sudo apt-get install sun-java6-jdk
``` or sun-java5-jdk.

3) Oracle support a lot of OSS initiatives, but there is no "free" version if that's what you are looking for. However, linux/ubuntu comes with MySQL which will suit your purpose for simple learning etc.

---

### Post by bumanie on 2008-04-04
I have a friend who successfully runs the internet through a usb connected modem in ubuntu. It should not be a problem.

---

