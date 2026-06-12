---
title: "help for Java problems"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by mconway0003 on 2006-12-29
I new to linux and i have been trying numerous times to install JRE. Following someone's instructions I used wget (which, by the way, i dont know what the difference is between wget and apt-get) to save the java-package. I used apt-get to install the package i think, and then proceeded to apt-get the debian file and it said it couldnt be found. I also dont understand why the instructions told me to install a file that i didnt get in the java package. 

See Below:
marcus@Marcus:~$ wget [http://davyd.ucc.asn.au/projects/misc/sun-j2sdk1.5_1.5.0_i386.deb](http://davyd.ucc.asn.au/projects/misc/sun-j2sdk1.5_1.5.0_i386.deb)
--16:27:59--  [http://davyd.ucc.asn.au/projects/misc/sun-j2sdk1.5_1.5.0_i386.deb](http://davyd.ucc.asn.au/projects/misc/sun-j2sdk1.5_1.5.0_i386.deb)
           => `sun-j2sdk1.5_1.5.0_i386.deb'
Resolving davyd.ucc.asn.au... 130.95.13.9
Connecting to davyd.ucc.asn.au|130.95.13.9|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://wiki.serios.net/wiki/Debian_Java_JRE/JDK_installation](http://wiki.serios.net/wiki/Debian_Java_JRE/JDK_installation) [following]
--16:28:00--  [http://wiki.serios.net/wiki/Debian_Java_JRE/JDK_installation](http://wiki.serios.net/wiki/Debian_Java_JRE/JDK_installation)
           => `JDK_installation'
Resolving wiki.serios.net... 75.126.27.156
Connecting to wiki.serios.net|75.126.27.156|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 24,145       144.85K/s             

16:28:01 (144.71 KB/s) - `JDK_installation' saved [24145]

marcus@Marcus:~$ sudo apt-get install java-package
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  debhelper dpkg-dev fakeroot html2text
Suggested packages:
  dh-make debian-keyring
The following NEW packages will be installed:
  debhelper dpkg-dev fakeroot html2text java-package
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 830kB of archives.
After unpacking 2834kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main dpkg-dev 1.13.22ubuntu7 [110kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main html2text 1.3.2a-3 [95.5kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main debhelper 5.0.37.3ubuntu4 [508kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main fakeroot 1.5.9ubuntu1 [94.7kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse java-package 0.27 [22.8kB]     
Fetched 830kB in 14s (56.1kB/s)       
Selecting previously deselected package dpkg-dev.
(Reading database ... 91606 files and directories currently installed.)
Unpacking dpkg-dev (from .../dpkg-dev_1.13.22ubuntu7_all.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3_i386.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_5.0.37.3ubuntu4_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.5.9ubuntu1_i386.deb) ...
Selecting previously deselected package java-package.
Unpacking java-package (from .../java-package_0.27_all.deb) ...
Setting up dpkg-dev (1.13.22ubuntu7) ...
Setting up html2text (1.3.2a-3) ...

Setting up debhelper (5.0.37.3ubuntu4) ...
Setting up fakeroot (1.5.9ubuntu1) ...

Setting up java-package (0.27) ...
marcus@Marcus:~$ sudo apt-get install sun-j2sdk1.5debian
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-j2sdk1.5debian
marcus@Marcus:~$ sudo apt-get install sun-j2sdk1.5debian
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-j2sdk1.5debian

any help would be most appriciated

Thanks
Marcus

---

### Post by DougieFresh4U on 2006-12-29
I will most likely be chastised from other members for saying the following: Have you tried installing Automatix 2 and getting java through that and many other things you might need. Sorry I do not know the link off hand, but there are many threads pertaining to Automatix 2.

---

### Post by jonathan.lees on 2006-12-29
You seem to be installing the JDK and not the JRE. The JDK is used for devolpment and compiling so you don't really need it. The graphical installer Automatix2 provides a Java JRE and JDK installation. If you head over to [Automatix]("http://www.getautomatix.com") you can download an installer for whatever version of Ubuntu you are using.

---

### Post by benuski on 2006-12-29
You need to get the universe and multiverse repositories, as said right [here]("https://wiki.ubuntu.com/AddingRepositoriesHowto").  In one of those, I can't remember which, is an already prepackged version of Sun's Java 5, ready for Ubuntu use.  When you get those activated, do 
```
sudo apt-get install sun-java5-bin
```
Then you should be good to go

---

### Post by mconway0003 on 2006-12-29
Thanks for all your replies. I actual did use automatix2 but there was still an error with installing JRE correctly. Also, benuski, when u said i should do sudo apt-get install sun-java5-bin, i was confused because i thought i needed to get packages with the ".deb" extension.:-k

---

### Post by Sef on 2006-12-29
Use Add/Remove to install Java.  Applications > Add/Remove > Search > Sun Java  > Click on Sun Java and the firefox plugin.  

Have you enabled the [repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu")?

---

### Post by benuski on 2006-12-29
When you use apt-get, you access one of Ubuntu's repositories, and everything in that repository is a ".deb" file, so the people who wrote it decided there was no need to have the redundancy of tacking on ".deb" to the end of the package name.  Also, once you enable the universe and multiverse repositories, you can just go to the Synaptic Package Manager and search for sun-java5-bin.  Synaptic is just the graphical way of doing "apt-get."

---

### Post by mconway0003 on 2006-12-29
> **mconway0003 said:**
> Thanks for all your replies. I actual did use automatix2 but there was still an error with installing JRE correctly. Also, benuski, when u said i should do sudo apt-get install sun-java5-bin, i was confused because i thought i needed to get packages with the ".deb" extension.:-k

i see, so what is the .bin extension for, is that the same .bin as in .bin/.cue???

---

### Post by benuski on 2006-12-29
Its not a ".bin" extension... technically, the file is "sun-java5-bin.deb".  They but the "-bin" to distinguish it from the other "sun-java5" packages, like "sun-java5-jdk" and "sun-java5-fonts".

---

