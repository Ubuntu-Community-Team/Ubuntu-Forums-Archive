---
title: "To run frostwire.."
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by rocketboys on 2007-05-21
I installed frostwire..

and I tried to run frostwire, but I'm getting this message.

danny@danny-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
danny@danny-desktop:~$ sudo apt-get install sun-java6-bin
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
danny@danny-desktop:~$ 

it was keep saying this so I went to java.com and downloaded the newest one

and installed it, but it would keep say that.

Help me please  :'(

Thank you!

---

### Post by jiminycricket on 2007-05-21
Install sun-java6-jre and sun-java6-plugin from Ubuntu multiverse (enable in Synaptic Settings->Edit Repositories) instead

If it still doesn't work, ```
sudo update-alternatives --config java
``` and choose the number of highest version of Sun Java.

---

### Post by wormser on 2007-05-21
Try uninstalling java then installing it again threw apt-get.  I have heard of problems trying to upgrade it.

This [link]("https://help.ubuntu.com/community/Java#head-7852ba79216c811b4345924d824bf15489ce7164") is about installing java on Ubuntu.

---

### Post by rocketboys on 2007-05-21
> **jiminycricket said:**
> Install sun-java6-jre and sun-java6-plugin from Ubuntu multiverse (enable in Synaptic Settings->Edit Repositories) instead

If it still doesn't work, ```
sudo update-alternatives --config java
``` and choose the number of highest version of Sun Java.

Thank you for your response!

I used the code you gave me and it's working now!

thank you so much :)

I can sleep now...ehehe

---

