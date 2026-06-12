---
title: "Not sure if anyone uses Fedora, NDISWrapper"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2008-03-06
Hi I use Fedora/ubuntu dual boot, and i have a  Broadcom BCM4318 network card, and it wont work out of the box, so i used a ndiswrapper

so i do this

```
gedit /etc/yum.conf
```
then i add
```
add ndiswrapper/bcm4318/windows/drivers
```
Then i get
```
Error, no drivers are found, you may want to try a different method
``` any ideas

---

### Post by igknighted on 2008-03-06
Where did you get those directions?

---

### Post by Crafty Kisses on 2008-03-06
Yeah, I've used Fedora before, and I beleive it'd go something like this, you're doing it totally wrong, not to sound rude or anything, but you are, do the following:
```
gedit /etc/yum.conf
```
After that, add the following lines to your config file:
```
[livna]
name=Livna for Fedora Core $releasever - $basearch - Base
baseurl=http://rpm.livna.org/fedora/$releasever/$basearch/RPMS.lvn
        http://livna.cat.pdx.edu/fedora/$releasever/$basearch/RPMS.lvn
        http://wftp.tu-chemnitz.de/pub/linux/livna/fedora/$releasever/$basearch/RPMS.lvn
        http://ftp-stud.fht-esslingen.de/pub/Mirrors/rpm.livna.org/fedora/$releasever/$basearch/RPMS.lvn
#mirrorlist=http://rpm.livna.org/mirrorlist
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-livna
```
Click on save and done. Now run this command to install ndiswrapper:
```
um install ndiswrapper kernel-module-ndiswrapper-$(uname -r)
```
You might want to be careful though, everytime you update your kernel, you need to re-install the NDISwrapper.
This is how it should look like when it's installing:
```
============================================================================
 Package                 Arch       Version          Repository        Size
=============================================================================
Installing:
 kernel-module-ndiswrapper-2.6.14-1.1637_FC4  i686       1.5-0.lvn.1.4    livna              81 k
 ndiswrapper             i386       1.5-0.lvn.1.4    livna              24 k

Transaction Summary
=============================================================================
Install      2 Package(s)
Update       0 Package(s)
Remove       0 Package(s)
Total download size: 105 k
Is this ok [y/N]: y
Downloading Packages:
(1/2): kernel-module-ndis 100% |=========================|  81 kB    00:02
(2/2): ndiswrapper-1.5-0. 100% |=========================|  24 kB    00:00
Running Transaction Test
Finished Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing: ndiswrapper                  ######################### [1/2]
  Installing: kernel-module-ndiswrapper-2. ######################### [2/2]

Installed: kernel-module-ndiswrapper-2.6.14-1.1637_FC4.i686 0:1.5-0.lvn.1.4 ndiswrapper.i386 0:1.5-0.lvn.1.4
```
After it installs, you need to create a folder in your home directory, then download the appropiate driver.
**From terminal cd folder or directory where the windows driver is now located:**
```
cd bcmwl
```
You then need to become root.
```
sudo -i
```
Then after that, do the following:
```
/usr/sbin/ndiswrapper -i bcmwl5.inf
```
Then it should look like this:
```
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
[root@FC4Laptop bcmwl]#
```
You might want to view the installation of driver:
```
/usr/sbin/ndiswrapper -l
```
If everything went well, it should turn out like this:
```
[root@FC4Laptop bcmwl]#/usr/sbin/ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
```
You NEED to create an alias in** /etc/modprobe.conf**
```
/usr/sbin/ndiswrapper -m
```
Then do the following:
```
[root@FC4Laptop bcmwl]# /usr/sbin/ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.conf
[root@FC4Laptop bcmwl]#
```
**Go to System Tools >Internet Configuration Wizard > enter root's password and select >Wireless Connection and DONE! :D**

Hopefully this works, any problems just let me know, I've set up tons of NDISwrappers haha. :)

---

