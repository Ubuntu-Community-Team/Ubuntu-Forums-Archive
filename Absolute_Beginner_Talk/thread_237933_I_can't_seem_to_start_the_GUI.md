---
title: "I can't seem to start the GUI"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by WilcoRogers on 2006-08-16
I apologise in advance for any stupidity, but I am new to linux, and I am trying to install it on an old laptop. I am using the 5.10 version (Breezy Badger), and I seemed to have no trouble installing it. I can log in in the shell, but i cannot start the GUI. I know there's something i'm missing, but i don't know what. Here are some things that may help:

It's an old computer so I don't have it connected to the internet.
It has very little hard drive space, but i all seemed to fit, so It should be alright.


Thank you for any help!

WilcoRogers

---

### Post by nalmeth on 2006-08-16
what happens when you type:
sudo aptitude update
sudo aptitude install ubuntu-desktop

If this installs some new packages, then likely you did a server install, which doesn't include the GUI. Don't worry about errors about connecting to sites, the GUI is on the CD aswell, and should be able to install off the CD.

Hopefully that works

---

### Post by WilcoRogers on 2006-08-16
well it seems that i have had a brain lapse and forgotten my password, although i am pretty sure i did a regular install, i will reinstall anyways, and make sure i don't - umm is there any advice i should have on partitions? i followed some online thing, and made a few partitions, so i know how to do it.. but what should i have?

---

### Post by nalmeth on 2006-08-17
If you haven't reinstalled yet, when you boot, and when you see GRUB loading, hit ESC, and go into recovery mode. 

You should be logged in as root, unless you have already created a seperate root user. You would know if you did.

To change your password, enter:
passwd username

username being your username of course.

From the root-console, you don't need to apphend sudo to the command, so you could just type:
aptitude update
aptitude install ubuntu-desktop

Make sure the Ubuntu CD is in the drive.

---

### Post by LadyDoor on 2006-08-18
This may seem drastic, but you might try reinstalling...this time with Dapper.

---

