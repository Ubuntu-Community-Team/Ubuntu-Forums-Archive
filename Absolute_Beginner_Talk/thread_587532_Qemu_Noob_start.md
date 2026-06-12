---
title: "Qemu Noob start"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2007-10-22
hey all,

wow is Gusty awesome. I was wondering if there were a tutorial (read- for beginners!! lol)on how to set up Qemu and virtualize Win XP within Gusty and partition Hard drives etc to prepare.

thanks all!

---

### Post by Maestro23 on 2007-10-22
This How-To is for Feisty, but it should shed some light.

[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo?highlight=%28Qemu%29](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo?highlight=%28Qemu%29)

Welcome to the forums and good luck.:)

---

### Post by JasonBourneLinux on 2007-10-22
k thanks! So I need a bit of clarification for these steps 

Create a group "kqemu" and add all users who should be allowed to use QEMU with acceleration to this group 

sudo addgroup --system kqemu
sudo adduser $USER kqemu 

therefore i would put in my username in USER (in all capitals?) 

Another step 

Create a virtual drive for Windows 

qemu-img create -f qcow windows.img 2G
This creates a two gigabyte virtual drive, stored as a single file called windows.img in THE LOCATION WHERE YOU RAN THE COMMAND. Any size above 1.5GB (the minimum to run Windows XP) is fine. The virtual drive will start out as a small file, and only fill its the size you specified when it reaches capacity due to the qcow file format used. 

How do I specify where I ran the command (im gonna use an existing NTFS partition) 

thanks all!!

---

