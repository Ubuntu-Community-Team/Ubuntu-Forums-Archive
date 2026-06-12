---
title: "Macbook - Dual Boot OSX and Ubuntu 9.10"
date: 2009-12-10
forum: Apple Hardware Users
---

### Post by rafaelbn on 2009-12-10
Hi everybody!

I'm trying to install Ubuntu 910 with OSX Leopard on my macbook black (v4.1 - early 2008). What happens is that rEFIt is not recognizing my linux installation. Here are the steps I have followed.

1- Fresh install OS X Leopard (no updates... Just out of the box)
2- Installed rEFIt v0.13 (default options)
3- Shutdown machine for 5 minutes
4- Turn it back on. rEFIt looks good. (just OS X option appears)
5- Under OS X, ran disk utility and resized my OS partition to 50GB (200GB avaiable after that)
6- Restarted with Ubuntu v910 x86 CD in and started live environment.
7- Started installation of ubuntu through the desktop shortcut.
8- Choose “install to the largest continuous free space"
9- After copying files, choose to install grub under sda3.
10- Restarted
11- Resync with rEFIt and shutdown machine.
12- After 5min, start it and no linux logo appears...

The main problem here I think it's something with the linux bootloader. rEFIt can't "see" any linux partition.

Am I missing something? I followed the guides from here and still no success...

Thanks!
Rafael

---

### Post by kstan_79 on 2009-12-10
try boot into live cd and repair grub.
I didn't install MBR at sda3 but sda. it still work. Base on documentation u shall install and your own Linux partition but it doesn't work with me.

Try with your own risk. By the way I use Macbook white 6,1

---

### Post by linuxopjemac on 2009-12-11
you can also try to sync the partition table from within rEFIt with partition tool.

---

### Post by tom4everitt on 2009-12-11
Yes, try to install grub to sda instead of sda3. Here's how you do it:

boot ubuntu live cd.
In terminal, write:
sudo grub
root (hd0,2)
setup (hd0)
quit

reboot. 

hopefully you will se an entry now. (Note that it will not look like a penguin, but rather like four gray squares or something, since refit doesn't recognize grub2 yet. It will say something like boot legacy os from hard drive.)

---

