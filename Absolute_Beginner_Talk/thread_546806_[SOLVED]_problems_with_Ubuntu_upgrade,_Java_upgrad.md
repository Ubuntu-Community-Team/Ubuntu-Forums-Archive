---
title: "[SOLVED] problems with Ubuntu upgrade, Java upgrade and Grub"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by &amp;wP*!) on 2007-09-09
**1. Ubuntu Upgrade from Edgy Eft to Feisty Fawn**

System->Administration->Update Manager has never shown me any information about upgrade to Feisty Fawn. That means, a version of Ubuntu does not support to upgrade to the next version of Ubuntu automatically. I have to install Feisty Fawn manually from scratch. Can you confirm this?

**2. Java Upgrade**
I have installed Edgy Eft but it has no Java. Firefox cannot find it. How shall I install it? Firefox asks me to install it but I am afraid of that install will be Firefox specific, but not operating system. If I for example install Opera later, will it then support that also?

**3. Grub**
After latest installations Grub shows me two kernels in the boot menu.
2.6.17-12-generic
2.6.17-10-generic
I think the first one is "Feisty Fawn" kernel, the 2nd one is Edgy Eft kernel, although I don't get this info during login sessions. Grub menu.lst contains two kernels, isn't it risky to use two different kernels? The operating system installation might not support one of them correctly. Can I delete one of these Grub entries? Shall I also delete the corresponding files  in the /boot?

Thanks you in advance.

---

### Post by Jimmyfj on 2007-09-09
First of all you might want to install a new version of Ubuntu from scratch. A clean install is always better than any update.

Second you can look for any java and flash in Programs/Add/Remove.

The difference in kernel versions is due to a kernel update your update manager has performed at some time since you first installed the system. Just a newer kernel. The other is your old kernel and is for boot up in recovery mode.

---

### Post by &amp;wP*!) on 2007-09-09
> **Jimmyfj said:**
> First of all you might want to install a new version of Ubuntu from scratch. A clean install is always better than any update.
Would you please can tell me a weblink how to install it? I have a dual boot machine but I don't have any clue how to uninstall a version and install a new version by keeping my /home /swap partitions?
> Second you can look for any java and flash in Programs/Add/Remove.
Operating system says me:
```
utku@utku-desktop:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
utku@utku-desktop:~$ 
```
Applications/Add/Remove says me that there is a Java plugin for Firefox/Mozilla. But [http://java.com](http://java.com) tells me that my machine does not have a JRE. Firefox does not have a option to point out a Java installation directory.
> The difference in kernel versions is due to a kernel update your update manager has performed at some time since you first installed the system. Just a newer kernel. The other is your old kernel and is for boot up in recovery mode.
There are entries already for recovery mode:
```
utku@utku-desktop:~$ grep title /boot/grub/menu.lst
title           Ubuntu, kernel 2.6.17-12-generic
title           Ubuntu, kernel 2.6.17-12-generic (recovery mode)
title           Ubuntu, kernel 2.6.17-10-generic
title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
title           Ubuntu, memtest86+
title           Other operating systems:
title           Microsoft Windows XP Home Edition
```
I am asking why there is another version of **kernel**, but not recovery mode. Shall I pay attention to these?

Thank you for the answers.

---

### Post by steve.horsley on 2007-09-09
1)
I can't help you upgrade - I've never done it. 
Assuming you have a separate /home partition, you can use the installer to install a new version. Choose custom partitioning, edit the partitions and change the mount points. Your / partition wants reformatting, and your /home partition wants mounting on /home but **not** formatting. Back up first, just in case.

2)
I would suggest installing packages sun-java6-jre and sun-java6-plugin. This should fix firefox for you. You will still have to install the plugin into Opera later by hand, if you install Opera.

3)
I think these are 2 kernels from the same release, though I'm not sure which. You get a second kernel listed in GRUB if you install a security upodate that updates the kernel. The idea is that if for some reason the updated kernel doesn't work on your machine, you can still use the old kernel. Once you are happy that the new kernel works OK, you can uninstall the old kernel by searching for linux-image in synaptic.

---

### Post by &amp;wP*!) on 2007-09-09
> **steve.horsley said:**
> 2)
I would suggest installing packages sun-java6-jre and sun-java6-plugin. This should fix firefox for you. You will still have to install the plugin into Opera later by hand, if you install Opera.

Hi Steve, thanks for the answer. Synaptic does not show me sub-java6-*, does it mean that it was introduced in 7.04 (Feisty Fawn)? I have 6.10 (Edgy Eft). Isn't it dangerous to install a package which has not been tested in a distro version which was not listed in Synaptic?

Thanks.

---

### Post by schorsch on 2007-09-09
Have you already tried to start an upgrade via
```
sudo update-manager -c
```
in a terminal session?

---

### Post by &amp;wP*!) on 2007-09-09
> **schorsch said:**
> Have you already tried to start an upgrade via
```
sudo update-manager -c
```
in a terminal session?
Hi schorsch, I have just tried it. -c shows me the Feisty Fawn now! Thank you!

---

