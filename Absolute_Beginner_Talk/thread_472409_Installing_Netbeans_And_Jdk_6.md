---
title: "Installing Netbeans And Jdk 6"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by jte091805 on 2007-06-13
Hello guys!

I'm completely new to Ubuntu world. I have installed Ubuntu 7.04 on my desktop and I'm loving it so much. How ever, I dont have access to the Internet so I can't use APT-GET INSTALL. Only thing is that I go to my office, download installer .bin files and try to install them on my standalone pc at home.

I installed bundle of Netbeans 5.5.1 and JDK 1.6.0_01.bin. The installer put the installation on /opt/jdk1.6.0_01 and opt/netbeans5.5.1. 

The installation was successful. Then I have to try compiling java programs in the terminal using "javac" command.
To my surprise, the console then displayed "type gij" options and whatever. In windows, after installing jdk, I have to add the path of jdk1.6.0/bin to environmental variables. What do I need to do to be able to use jdk and compile my java programs.

Need help.... thanks a lot

---

### Post by sankarv on 2007-06-13
set the PATH variable to point to <java folder>/bin directory as follows:


> export PATH=$PATH:/<java folder>/bin

add the above entry in your **.bashrc** file in ur home directory (here <javafolder> refers to ur full path to the java folder containing the bin folder) .


also if needed put another entry for CLASSPATH too.



logout and login again. 

it should work.

u can check as, try 


> which javac



this will display the path for the command used.

---

### Post by jte091805 on 2007-06-13
Hey. Thanks. I'll try it as soon as i go home. I'll email you tomorrow thanks again

---

### Post by jte091805 on 2007-06-13
Hello again. How am I going to put entry for CLASSPATH? where is it located? 

Thanks again.

---

### Post by koushic_dk on 2007-06-13
You can use "/usr/sbin/update-alternatives " to change gij to sunjdk

The help will be displayed on how to use --install option. This is used to install the altenative java in the path .
the --config option would help making the JDK 6 as active.

By this method , one can install more than 1 version of java viz JDK5 JDK1.4 etc and control the active version at any time.

Similairly you can add javac, rmiregistry rmid etc also using update-alternatives

---

