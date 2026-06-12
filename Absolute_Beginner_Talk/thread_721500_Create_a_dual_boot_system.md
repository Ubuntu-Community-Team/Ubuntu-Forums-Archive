---
title: "Create a dual boot system"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Oldsterman on 2008-03-11
I have already installed Ubuntu 7.10 and would now like to install PCLinuxOS alongside it to create a dual boot system using the "live" GParted CD. Would someone like to help me accomplish please.

---

### Post by louieb on 2008-03-11
Dual booting 2 Linux distros isn't much different from dual booting XP and Linux. Heres a couple of places to start your education on partitions and gparted.
[Linux.com :: Dual-booting Windows and Linux the easy way (Linux.com videos)]("http://www.linux.com/feature/114157") Good video on using gparted - just think of widows being another Linux distro.
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") Screen shots of what gparted can do.
[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")
And of course the [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

---

### Post by sandysandy on 2008-03-11
here are some links to dual booting:-

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

the linux distro u install later will make entry for the previous distro in its menu.lst file.

regards

---

### Post by dstew on 2008-03-11
I don't know much about PCLinuxOS, but it looks like it installs from a Live CD like Ubuntu. My guess is that it will have a partitioning step, and give you a dual boot option too. But I am not sure about that, and the PCLinuxOS web site is not very helpful.

---

### Post by forrestcupp on 2008-03-11
> **dstew said:**
> I don't know much about PCLinuxOS, but it looks like it installs from a Live CD like Ubuntu. My guess is that it will have a partitioning step, and give you a dual boot option too. But I am not sure about that, and the PCLinuxOS web site is not very helpful.

Yeah, just try installing it first.  It probably will make and set up partitions during the install, just like Ubuntu does.  If not, then you can worry about GParted LiveCD.

---

### Post by Oldsterman on 2008-03-11
Sorry for being so thick but, you say i should reboot the computer with the PCLinuxOS CD and just follow and accept whatever it suggests during the install?

---

### Post by dstew on 2008-03-11
Well, don't just accept everything it says uncritically. If it wants to use the whole drive, then no, do not accept that. If it has an option to shrink the Ubuntu partition, and then use the new unallocated space, that would be all right. But, I don't know anything about installing PCLinuxOS. Maybe try the forums on their site.

---

### Post by louieb on 2008-03-11
[PCLinuxOS]("http://www.pclinuxos.com/") is a good distro. I had it installed but I don't care for KDE so now its gone. I tried quite a few distros before deciding Ubuntu was best for me.
 As a rule of thumb I use GParted to setup my partitions before running any installer.  Every installer I've tried has some manual way of telling it where you want it installed. You can do that with PCLinuxOS too. 

PCLinuxOS uses the Disk Drake partitioner. I don't care for Disk Drake, it can alter your partition table in a non-standard way. For example it can put a primary partition inside an extended partition (on logical partitions should be inside an extended partition). 

[IMG]http://louboldt.com/ptwocents.gif[/IMG]Use GParted to setup you partitions ahead of install time and every thing will go just fine.

---

