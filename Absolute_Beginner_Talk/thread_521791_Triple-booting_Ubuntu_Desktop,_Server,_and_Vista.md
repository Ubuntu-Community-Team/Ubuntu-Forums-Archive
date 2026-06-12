---
title: "Triple-booting Ubuntu Desktop, Server, and Vista"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by thefowlstar on 2007-08-09
I have a HP Pavillion a1010n PC, with GRUB as the bootloader and Edgy and Vista both installed. I want to install Ubuntu Server for testing purposes and was wondering if it would be possible.

Here's my current configuration: (There's no more free space on the drive but I can shrink the storage partition if needed.)
Partition 1 (22g)	ext3		Ubuntu 6.10 Desktop Edition
Partition 2 (3g)	linux-swap
Partition 3 (40g)	ntfs		Windows Vista
Partition 4 (86g)	fat32		Storage

I can't install Ubuntu Server now because I've used up all 4 of my primary partitions. I've heard about something called Extended Partitions and was wondering if it would be possible to make one.

Here are the questions I have now:
	Is it possible to share swap space between 2 versions of Linux? (in this case Ubuntu Desktop and Ubuntu Server)
	Will making an extended partition mess up GRUB?

I also have no problem formatting my entire HD as all my data is backed up.

---

### Post by tjsullivan1 on 2007-08-09
Is there any particular reason why you need Ubuntu server edition? You could install all the server applications that you need on Ubuntu 6.10 Desktop through the command line. I have found that I actually like doing this on my primary workstation since it eliminates the need for me to have a second computer for web browsing for help files (don't get me wrong lynx and links are great, but some sites don't work through the command line). Moreover, since it seems like you are using this as a workstation anyway it may be more practical for you to just install the server applications like you would with Ubuntu Server installed but through the gnome-terminal instead of the command line interface.

---

### Post by bren on 2007-08-09
yes, convert one of your 4 primary to extended

then you can create as many logical partitions (within the extended as you need - no limit to   4 anymore - see wikipedia)

the easiest way is if you can back up one of your partitions to an external drive then convert it to extended perhaps....

back up all data before doing partition resizing!  1 time in 100 you will need it..

bren

---

### Post by thefowlstar on 2007-08-09
Actually, I'm thinking of converting this into a File Server permanently, but was just trying to make sure that everything works. I use Windows Vista now because I don't have enough money to go out and buy Windows Server Edition. I just shared my entire Storage partition in Windows and it seems to work just as well.

The problem is that we have 2 laptops in the house, one running Windows and the other running Ubuntu, and I can't access the files on the server with the Ubuntu laptop.

I've heard of installing the server packages to the Desktop Edition, but (correct me if I'm wrong) people have told me that it's simpler to just install the Server Edition. And since I have this spare computer just lying around, I thought I might just dedicate it as a file server.

And I appreciate the quick reply. :]

---

### Post by tjsullivan1 on 2007-08-09
If you did just want to use it strictly as a server, than you would be best off to just do a fresh install. I thought that you wanted it as a workstation since you had all of the other stuff (Ubuntu Desktop, Vista). I would recommend that since you already have the Desktop version installed, configure a Samba server on it to get some experience (this is how I did my first file server) and then reinstall with a server edition to save hard disk space. This will also allow you to test to make sure that your server can be reached from both your Ubuntu and Windows laptops (I've never connected my Ubuntu box to a Samba server, but I can't see why it wouldn't work with the mount command or connect to server in your desktop version).

---

### Post by p_quarles on 2007-08-09
The main difference between the desktop version and the server edition is that the latter does not install X by default. There are a few other minor differences, but in terms of functionality, you can learn about and test all server operations using the desktop version.

---

