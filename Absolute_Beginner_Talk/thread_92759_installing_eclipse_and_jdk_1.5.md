---
title: "installing eclipse and jdk 1.5"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by myd on 2005-11-20
Hello everyone,

I have installed eclipse and when i launch it i cant do anything, i cant create projects and so on. Also when i click on preferences it says "unable to create the selected preference page".

First i installed the jdk 1.5 following this guide:
[https://wiki.ubuntu.com/JavaAMD64](https://wiki.ubuntu.com/JavaAMD64)

When i do java -version it says that i have installed the 1.4 version (yes, i installed jdk 1.5).

then i installed eclipse:
[https://wiki.ubuntu.com/EclipseIDE](https://wiki.ubuntu.com/EclipseIDE)

i also modified my home .bahsrc and added the following lines:
#JDK 1.5
export JAVA_HOME=/usr/java/jdk1.5.0_05
export PATH=$JAVA_HOME/bin:$PATH

But still does not work...can someone help me please? i am really stuck at this...

Thanks in advance

---

### Post by SumoJim on 2005-11-20
I can't do it either.

If you have Eclipse at least showing you the text editor you should be able to change the option from 1.4 to 1.5 when you create a new project. (Look for a drop box option when the pop-up screen appears when the new project option is selected) Hopefully that's your only problem.

I am also trying to install Eclipse and jdk 1.5 and am having trouble. Did you get 1.4 to install properly? I downloaded 1.5 and didn't mess with 1.4 but I don't think 1.5 is installed. I tried downloading:

jdk-1_5_0_05-linux-i586.bin
and
jdk-1_5_0_05-linux-i586-rpm.bin

But both give me ther message:
The filename "jdk-1_5_0_05-linux-i586-rpm.bin" indicates that this file is of type "unknown". The contents of the file indicate that the file is of type "shell script". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "shell script", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

Though I don't know what "shell script" is I don't know what extension I should change it to, I don't even know what a .bin file is.

When I try to run Eclipse I ge tthe message:
A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/home/sumojim/Desktop/SumoJim/Programs/Eclipse/eclipse-SDK-3.1.1-linux-gtk.tar.gz_FILES/eclipse/jre/bin/java
'java' in your current PATH

---

### Post by myd on 2005-11-20
Well, it seems that 1.4 was already installed in ubuntu, i haven't really tried to deal with it. So i downloaded jdk-1_5_0_05-linux-amd64.bin from sun.com and installed it, but my try was worthless, no luck (when i do java -version it says that 1.4 is installed).

Maybe i should try and uninstall 1.4 but i don't know how :confused: .

About eclipse, only the main window shows up, i can't even create a new project.

I am totally lost :mad:

---

### Post by steve.horsley on 2005-11-20
[QUOTE=myd]Hello everyone,

I have installed eclipse and when i launch it i cant do anything, i cant create projects and so on. Also when i click on preferences it says "unable to create the selected preference page".

First i installed the jdk 1.5 following this guide:
[https://wiki.ubuntu.com/JavaAMD64](https://wiki.ubuntu.com/JavaAMD64)

When i do java -version it says that i have installed the 1.4 version (yes, i installed jdk 1.5).

then i installed eclipse:
[https://wiki.ubuntu.com/EclipseIDE](https://wiki.ubuntu.com/EclipseIDE)

i also modified my home .bahsrc and added the following lines:
#JDK 1.5
export JAVA_HOME=/usr/java/jdk1.5.0_05
export PATH=$JAVA_HOME/bin:$PATH

But still does not work...can someone help me please? i am really stuck at this...

Thanks in advance[/QUOTE]

If the java version is your problem, I think I can help. If you user the command **which java**, it will probably tell you /usr/bin/java. If you look at that, it's probably a link to /etc/alternatives/java (**ls -l /usr/bin/java**). If you look at this, it's probably a link to the old 1.4 blackdown java that Ubuntu installs. So you need to replace that link with a link to the later java. These commands do that:
[B]sudo mv /etc/alternatives/java /etc/alternatives/java-original
sudo ln -s /usr/java/jdk1.5.0_05/jre/bin/java /etc/alternatives/java[/B]
Please check the path I gave in the second command - I guessed

Steve

---

### Post by myd on 2005-11-20
Thank you very much Steve, now is working correctly :) 

Thanks again for the help

---

