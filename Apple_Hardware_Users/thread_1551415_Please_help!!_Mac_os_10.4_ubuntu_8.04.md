---
title: "Please help!! Mac os 10.4 ubuntu 8.04"
date: 2010-08-12
forum: Apple Hardware Users
---

### Post by Thuck on 2010-08-12
So I downloaded ubuntu not knowing it was totally take over my Mac. I'm nervous it may have deleted everything off my memory and now idk how to get it back! When I start it up it boots with ubuntu only! How do I get it to boot up the Mac os? And did installing this delete everything from my harddrive/partition!?

Please help!

---

### Post by Grafens on 2010-08-12
Restart your computer, when you see the "Grub" boot loader screen appear use the up and down arrows on your keyboard to select which operating system you want to use.

---

### Post by Thuck on 2010-08-12
> **Grafens said:**
> Restart your computer, when you see the "Grub" boot loader screen appear use the up and down arrows on your keyboard to select which operating system you want to use.

The grub bootloader doesn't pop up. It say push l for something/Linux or c to boot CD rom. I push l and ubuntu comes up

---

### Post by Paul S on 2010-08-12
You know you're using a 2 year old ubuntu, so things are a bit different now.  I'm not sure I recall all the stuff from 2 years ago.

Unless you selected to use your entire disk when the installation promted for partitioning advice, then your mac partition is still there.  But you probably have a hidden grub screen and you're not seeing the option to select it.

Post the contents on /boot/grub/menu.lst file and the output from this command in a terminal:

sudo fdisk -l

Also, if there is a file called /etc/default/grub, post it's contents also.

From these we should be able to help you make your grub menu appear when you're booting.

Take a look at these files yourself, and it may be self explanatory of how to edit them.

---

### Post by BriceHulse on 2010-08-12
When your computer first boots up, hold down the option key until you see two hard drive icons. Use the arrow keys or the mouse to select the Mac OS X one. This will boot you into Mac OS X. From your Mac OS X account, you can open Disk Utility */Applications/Utilities/Disk Utility.app* and remove the Ubuntu partition-that is, if you don't want it. The Ubuntu partition is probably */dev/sda3*.

---

### Post by Thuck on 2010-08-12
> **BriceHulse said:**
> When your computer first boots up, hold down the option key until you see two hard drive icons. Use the arrow keys or the mouse to select the Mac OS X one. This will boot you into Mac OS X. From your Mac OS X account, you can open Disk Utility */Applications/Utilities/Disk Utility.app* and remove the Ubuntu partition-that is, if you don't want it. The Ubuntu partition is probably */dev/sda3*.

Ok so I got it to come up but my Mac os isn't there... Did all my information get deleted!?

---

### Post by shawnhcorey on 2010-08-13
> **Thuck said:**
> The grub bootloader doesn't pop up. It say push l for something/Linux or c to boot CD rom. I push l and ubuntu comes up

First, the bootloader for PPCs is yaboot, not GRUB.

After you press 'l', there should be another screen where you can choose which variation of the OS to load.  Press TAB to get a list of all of them.  One of them should be your old OSX.  If not, you have installed Ubuntu over top of it.  In that case, you will have to reinstall OSX in another boot partition.

---

