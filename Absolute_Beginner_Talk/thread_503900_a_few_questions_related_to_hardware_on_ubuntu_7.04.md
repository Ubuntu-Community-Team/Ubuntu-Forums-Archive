---
title: "a few questions related to hardware on ubuntu 7.04"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by rustix on 2007-07-18
well i've installed Ubuntu 7.04 ( as you may have already figured) and i'm new to linux as well.. i have a few questions relating to hardware and would greatly appreciate anyone who could help me out....

**Question**

1.) When you connect a USB device such as a printer or modem how would you know it's been detected?
2.) Would a device (USB and/or otherwise) which does not have drivers for Ubuntu be detected or would it remain undetected?
3.) Do drivers vary for each and every version of linux (e.g. redhat, ubuntu, mandrake, etc.) or are they the same? i.e. (as an example) could you use redhat drivers for a particular device on ubuntu as well?
4.) Is it possible to force a new hardware detection? If so how?
5.) How could you manually install drivers on Ubuntu?
6.) Does anyone know of any common/famous USB modems and routers which are  compatible on Ubuntu?
7.) Does anyone know whether the Binatone ADSL 500 USB modem is supported on Ubuntu? According to the box it is supported in linux but when I plugged it in, it wasn't detected!?

well that's about it for the moment.. hope someone could help me out :)

---

### Post by Cypher on 2007-07-18
1) Open a terminal and type "dmesg", this will show you the system messages and the last few should be from the USB subsystem about whatever device you plugged in.
2) The USB system will detect that a USB device was plugged in and make it available. If it's a device that needs some extra driver for proper functionality, those will have to be loaded after.
3) Realize that the Kernel (the heard of Linux) is uniform across all distributions. The various distos (Redhat, Ubuntu) alter the persentation, but the heart is the same. So as long as you find a driver for your specific version of the Kernel, you can use it.
4) As long as the driver for whatever device you are trying to plug in is installed, you shouldn't have to manually do anything
5) Drivers are usually *.KO files that you would "insmod" manually to test and then add to /etc/modules file to load automatically each time you boot up.
6) No clue on this one
7) Search for "ADSL USB" and you'll find countless  posts of people who've got things working..

---

### Post by Majorix on 2007-07-18
1. lsusb from terminal.
2. undetected.
3. all use the same drivers.
4. Force? You mean drivers?
5. using Synaptic.
6. Well most of them are recognized under Ubuntu. I myself use a USRobotics modem for example and it works fine.
7. I never heard of that modem, sorry :(

---

### Post by rustix on 2007-07-18
so using **lsusb** i found that the modem was detected but how do i install the drivers from the CD?

also when any new device is detected by ubuntu, does it automatically display a dialog box assisting to install the drivers (like in Windows) or do the drivers have to be installed manually..

**@Majorix**

about the 4th questions.... what i meant was is it possible to force ubuntu to search for and detect any newly connected devices and display what they are...

and how do use synaptic?? it's confusing....

---

### Post by CautionaryX on 2007-07-18
Just open up synaptic and press F1. It opens up a manual that has screenshots and everything.

---

### Post by rustix on 2007-07-18
how do you mount a ntfs hard disk? and have rights to access and modify files in it?

---

### Post by Golyadkin on 2007-07-18
The easiest way to mount NTFS harddisks is by installing ntfs-g3 and ntfs-tools. Then the NTFS disks will be automatically mounted with read / write support.

---

### Post by nelamvr6 on 2007-07-18
> **rustix said:**
> how do you mount a ntfs hard disk? and have rights to access and modify files in it?


It should be already mounted if it's installed in your system. Check in the /media folder, it'll likely be called sda1 or something similar.

I don't think that Linux can write to ntfs partitions.  Reading and copying is no problem though.

One thing you might consider doing is creating a small partition and formating it in fat32, that way there is a place where both windows and Linux can write things.

---

### Post by Golyadkin on 2007-07-19
Writing to NTFS is no problem at all for Ubuntu, it is very functional and I have been using it daily for months now.

---

### Post by rustix on 2007-07-19
what is ntfs-g3 and ntfs-tools and how do i install it??

---

### Post by 3rdalbum on 2007-07-19
> **rustix said:**
> what is ntfs-g3 and ntfs-tools and how do i install it??

ntfs-3g is a kind of driver, ntfs-tools is a set of programs.

You install them using Synaptic Package Manager.

---

### Post by Golyadkin on 2007-07-19
they are packages that contain the tools you need to mount NTFS partitions with read/write support in ubuntu. They are in the official repositories.
Install them by typing this in a terminal window:
> 
sudo apt-get install ntfs-3g ntfs-tools


---

### Post by rustix on 2007-07-19
i get the following error 

```

E: Couldn't find package ntfs-3g

```

what does is it mean? what do i have to do?

by the way do the ntfs partitions become writable the moment these are installed?? or do i have to do something else as well??

---

### Post by Golyadkin on 2007-07-21
Check this guide, it will show you exactly how to do this, the easy way: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

