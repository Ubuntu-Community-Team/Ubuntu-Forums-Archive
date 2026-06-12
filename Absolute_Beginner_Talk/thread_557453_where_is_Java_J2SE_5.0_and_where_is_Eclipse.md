---
title: "where is Java J2SE 5.0 and where is Eclipse?"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by spearfish on 2007-09-22
Ok, I just installed Ubuntu 7.04 on my Dell desktop, and using the Synaptic Package Manager, I installed the following:

1.  sun-java5-jdk  (Sun Java 5.0 development kit)
2. ecj  (Standalone version of Eclipse)

What I'm wondering is, where IS this stuff?  Eclipse doesn't show up under Applications->Programming.  Also, when I type "java -showversion" in a terminal window, it says I am running java 1.4.  Huh?  Why doesn't it say I'm running J2SE 5.0 ?

Thanks for ANY help on this!

---

### Post by agurk on 2007-09-22
I'm no expert, but it looks to me as if your default java is the gij that comes with Ubuntu. To select another as default, run: **sudo update-alternatives --config java** (more info [here](https://help.ubuntu.com/community/Java)).

I know nothing about ecj, but the description in Synaptic mentions it being a standalone version of the JDT *compiler* in Eclipse, not Eclipse itself. This smells command line application to me, and not something that would be available from the Applications menu.

---

### Post by conehead77 on 2007-09-22
when i type "eclipse" in the terminal, it launches.
you can find the file under /usr/bin/

dunno about the java stuff

---

### Post by spearfish on 2007-09-22
Well, after doing a little forum searching, I think I found the right command to make Ubuntu use the latest version of Java.  I did it by typing:

sudo update-java-alternatives -s java-6-sun

It went through and changed all the dependencies or links or whatevers to Java 6.  Yay!  I compiled a Hello World program under Java 6 and it seems ok.

Just to be sure, I typed "java -version" and got this:

user@Computer:~/programs/java$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)


As for Eclipse, this is what I get when I type "eclipse" at the command prompt:

user@Computer:~/programs/java$ eclipse
The program 'eclipse' is currently not installed.  You can install it by typing:
sudo apt-get install eclipse
Make sure you have the 'universe' component enabled
bash: eclipse: command not found
user@Computer:~/programs/java$ 

SO, I did just that:

user@Computer:~/programs/java$ sudo apt-get install eclipse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  eclipse-source
Recommended packages:
  eclipse-gcj
The following NEW packages will be installed:
  eclipse eclipse-source
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.2MB of archives.
After unpacking 37.1MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe eclipse-source 3.2.2-0ubuntu3 [30.0MB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe eclipse 3.2.2-0ubuntu3 [128kB]
Fetched 30.2MB in 2m23s (210kB/s)                                              
Selecting previously deselected package eclipse-source.
(Reading database ... 121339 files and directories currently installed.)
Unpacking eclipse-source (from .../eclipse-source_3.2.2-0ubuntu3_i386.deb) ...
Selecting previously deselected package eclipse.
Unpacking eclipse (from .../eclipse_3.2.2-0ubuntu3_i386.deb) ...
Setting up eclipse-source (3.2.2-0ubuntu3) ...
Setting up eclipse (3.2.2-0ubuntu3) ...

AND Hooray!  Eclipse magically appears under Applications->Programming with a nice blue icon.

Now, why the heck doesn't that happen when you use the Synaptic Package Manager?  What GOOD is the Synaptic Package Manager?

Thanks to the folks above for your responses, by the way.  Cheers to the Ubuntu community!

:)

Thanks guys!

---

### Post by agurk on 2007-09-22
> **spearfish said:**
> Now, why the heck doesn't that happen when you use the Synaptic Package Manager?  What GOOD is the Synaptic Package Manager?
Well, it does, if you install Eclipse and not ecj. :) Glad you're up and rollin'!

---

