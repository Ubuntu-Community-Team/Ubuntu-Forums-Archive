---
title: "JRE installation"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by vivin_west on 2006-12-11
I have downloaded the following software
jre-1_5_0_10-linux-i586.bin
 I want to know how to install this package.

---

### Post by vivin_west on 2006-12-11
I have downloaded this software

jre-1_5_0_10-linux-i586.bin( Java run time environment)

As per the download instructions I typed the following code,

vivin@vivin-desktop:~$ sudo apt-get install java-package
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package
vivin@vivin-desktop:~$

I am unable to proceed
I want to know how to install this package. Kindly let me know how to proceed.

---

### Post by xyz on 2006-12-11
[You could check this out]("http://ubuntuforums.org/showthread.php?t=76754")
OR
[Automatix]("http://www.getautomatix.com")
Good luck!

---

### Post by mvaniersel on 2006-12-11
Open a terminal
Go to the directory where you downloaded the package, and type:

chmod +x jre-1_5_0_10-linux-i586.bin
./jre-1_5_0_10-linux-i586.bin

good luck!

---

### Post by vivin_west on 2006-12-11
Thanks

---

### Post by Sef on 2006-12-11
As long as you open [multiverse repository]("https://wiki.ubuntu.com/AddingRepositoriesHowto"), you can download java directly from Add/Remove.  (Applications Add/Remove > search > Sun Java 5.0.)

---

### Post by igknighted on 2006-12-11
Using the method outlined by Sef is **by far** the best way to go.  When java 1.6 comes out in a few months, you will probably want to upgrade.  Apt/synaptic can do this for you, all you would need to do is click OK.  Or if there are any issues it can be easily removed.  Using the binary installer from the sun website works, but it is a rather crude installation tool and once you have installed it you are rather stuck without a lot of work to undo it.

**Always check for a program in any available repository to install before using a binary installer**

---

### Post by unisol on 2006-12-11
you could try this:Code:
cd ~/Desktop
chmod 755 jre-1_5_0_09-linux-i586-bin
sudo mv jre-1_5_0_09-linux-i586-bin  /opt
cd /opt
sudo ./jre-1_5_0_09-linux-i586-bin
sudo update-alternatives --config java
(use the arrow keys to move down the version 1.5)
java -version

---

### Post by Ben Sprinkle on 2006-12-11
```

sudo apt-get install java-common
sudo apt-get install fakeroot
fakeroot make-jpkg jre-1_5_0_10-linux-i586.bin

```
Then install it.

---

