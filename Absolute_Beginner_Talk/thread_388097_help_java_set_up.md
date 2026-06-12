---
title: "help java set up?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by zyx on 2007-03-19
Hi, there,

I use kubuntu 6.10. I have a trouble to set up java.
I download jre-1_5_0_11-linux-i586.bin from [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)
I use command as follows:
sudo mkdir /usr/java
sudo cp jre-1_5_0_11-linux-i586.bin /usr/java
cd /usr/java
sudo ./jre-1_5_0_11-linux-i586.bin

Do you agree to the above license terms? [yes or no]
 yes
Unpacking...
Checksumming...
0
0
Extracting...
./jre-1_5_0_11-linux-i586.bin: 310: ./install.sfx.8082: not found
cd: 632: can't cd to jre1.5.0_11

Done.

What is the problem install.sfx.8082?   Does anyone give me some clue? Thanks!

---

### Post by giftnudel on 2007-03-19
Hi,

what is wrong with the versions in the repositories which you can get with
```
sudo aptitude install  sun-java5-jdk
``` or
```
sudo aptitude install  sun-java5-jre
```

Whichever you want. I would really recommend to use those.

giftnudel

---

### Post by zyx on 2007-03-19
Thanks you your reply,
however, I also have an error:

sudo aptitude install  sun-java5-jdk
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are BROKEN:
  j2re1.4-mozilla-plugin
The following NEW packages will be automatically installed:
  sun-java5-bin sun-java5-demo
The following NEW packages will be installed:
  sun-java5-bin sun-java5-demo sun-java5-jdk sun-java5-jre
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.1MB/37.5MB of archives. After unpacking 99.2MB will be used.
The following packages have unmet dependencies:
  j2re1.4-mozilla-plugin: Depends: j2re1.4 but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
j2re1.4 [1.4.2.02-1 (edgy)]

Score is -19

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  j2re1.4 sun-java5-bin sun-java5-demo
The following NEW packages will be installed:
  j2re1.4 sun-java5-bin sun-java5-demo sun-java5-jdk sun-java5-jre
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.1MB/59.8MB of archives. After unpacking 160MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 edgy/multiverse sun-java5-demo 1.5.0-08-0ubuntu1 [52
50kB]
Get:2 edgy/multiverse sun-java5-jdk 1.5.0-08-0ubuntu1 [486
8kB]
Fetched 10.1MB in 1s (9173kB/s)
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p
rocess
(Reading database ... 129552 files and directories currently installed.)
Unpacking j2re1.4 (from .../j2re1.4_1.4.2.02-1_amd64.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p
rocess
dpkg: error processing /var/cache/apt/archives/j2re1.4_1.4.2.02-1_amd64.deb (--u
npack):
 subprocess pre-installation script returned error exit status 1
Unpacking sun-java5-bin (from .../sun-java5-bin_1.5.0-08-0ubuntu1_amd64.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p
rocess
dpkg: error processing /var/cache/apt/archives/sun-java5-bin_1.5.0-08-0ubuntu1_a
md64.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Unpacking sun-java5-jre (from .../sun-java5-jre_1.5.0-08-0ubuntu1_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p
rocess
dpkg: error processing /var/cache/apt/archives/sun-java5-jre_1.5.0-08-0ubuntu1_a
ll.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Selecting previously deselected package sun-java5-demo.
Unpacking sun-java5-demo (from .../sun-java5-demo_1.5.0-08-0ubuntu1_amd64.deb) .
..
Selecting previously deselected package sun-java5-jdk.
Unpacking sun-java5-jdk (from .../sun-java5-jdk_1.5.0-08-0ubuntu1_amd64.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p
rocess
dpkg: error processing /var/cache/apt/archives/sun-java5-jdk_1.5.0-08-0ubuntu1_a
md64.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/j2re1.4_1.4.2.02-1_amd64.deb
 /var/cache/apt/archives/sun-java5-bin_1.5.0-08-0ubuntu1_amd64.deb
 /var/cache/apt/archives/sun-java5-jre_1.5.0-08-0ubuntu1_all.deb
 /var/cache/apt/archives/sun-java5-jdk_1.5.0-08-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of sun-java5-demo:
 sun-java5-demo depends on sun-java5-jre (= 1.5.0-08-0ubuntu1); however:
  Package sun-java5-jre is not installed.
 sun-java5-demo depends on sun-java5-jdk (= 1.5.0-08-0ubuntu1); however:
  Package sun-java5-jdk is not installed.
dpkg: error processing sun-java5-demo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of j2re1.4-mozilla-plugin:
 j2re1.4-mozilla-plugin depends on j2re1.4; however:
  Package j2re1.4 is not installed.
dpkg: error processing j2re1.4-mozilla-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java5-demo
 j2re1.4-mozilla-plugin


What do I do? Any clues? Thanks!

---

### Post by AstorKole on 2007-03-19
Hello. I am also trying to set up java, and am having problems.

I downloaded "jre-1_5-0_11-linux-amd64.bin" onto my desktop.

I entered the following into terminal:
sudo cp jre-1_5_0_11-linux-amd64.bin /usr/java

And got this:
cp: cannot stat `jre-1_5_0_11-linux-amd64.bin': No such file or directory

Again, "jre-1_5-0_11-linux-amd64.bin" is on my desktop. Any help?

---

### Post by xyz on 2007-03-19
There's a good howto here on [Custom Installation of Sun Java]("http://ubuntuforums.org/showthread.php?t=319138&highlight=java")

---

### Post by nudnik on 2007-03-19
> **AstorKole said:**
> Hello. I am also trying to set up java, and am having problems.

I downloaded "jre-1_5-0_11-linux-amd64.bin" onto my desktop.

I entered the following into terminal:
sudo cp jre-1_5_0_11-linux-amd64.bin /usr/java

And got this:
cp: cannot stat `jre-1_5_0_11-linux-amd64.bin': No such file or directory

Again, "jre-1_5-0_11-linux-amd64.bin" is on my desktop. Any help?

Ubuntu is too dense to realise the file might exist outside of the current directory. To remedy this, type : cd Desktop. Now you can manipulate the file. 

Another problem: "/usr/java" usually doesnt exist by default; you have to manufacture it thusly: mkdir /usr/java

You should be doing all of the above with root access to avoid permissions annoyances. Accomplish that by typing " sudo -s" and then your password before performing any of these operations. Good luck! See mascot below.

---

### Post by AstorKole on 2007-03-19
I'm using Xubuntu 6.06 and the default File Manager, Thunar, doesn't give me the option of allowing the binaries to run as executables. At least not that I can see.

Edit: 

I tried "cd desktop" as you said, nudnik, and got this:

bash: cd: desktop: No such file or directory

Is that even possible??? lol

---

### Post by nudnik on 2007-03-19
> **AstorKole said:**
> I'm using Xubuntu 6.06 and the default File Manager, Thunar, doesn't give me the option of allowing the binaries to run as executables. At least not that I can see.

Edit: 

I tried "cd desktop" as you said, nudnik, and got this:

bash: cd: desktop: No such file or directory

Is that even possible??? lol

You have underestimated just how truly dense a command line can be :mrgreen: You failed to capatilise "Desktop". I know, I know. I want to throttle Ubuntu some times as well. Please, feel free. It helps. 

To make the file executable, open a terminal and type "chmod a+x"  followed by the filename. If your breathing becomes erratic, remember the mascot (see below) this is a normal end user experience :popcorn:

---

### Post by AstorKole on 2007-03-19
It worked!!! Java is installed!!!

/me bows to nudnik.

Thanks alot. Without your help i would be /head-desking right about now.:lolflag:

---

