---
title: "New drive, partition for dual boot from the start?"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by WATRD on 2006-04-17
Hi, I posted in the laptop section since that is the kind of machine I am building out, but then I spotted this section and my post probably should have gone here.  My appologies.

I am building out a laptop with a new drive.  I have already played with Ubuntu on the machine, so I know it works and I am going to be happy with it.  However, I still have to have windows.  So, I would like to dual boot until I can break the windows habit.

Since I am setting up a drive from scratch, do I have to do the set up xp, then allow Unbuntu to create a partition out of free space thing?  Or can I set up the partitions in advance, then just install the OS's to the corrrect partition and be on my way.  I have read the tutorials on dual booting with xp already installed, but it seems like since I am at zero anyway, there's got to be a better way.

Can you direct me to a tutorial that will tell me how to set up a dual boot system when I have blank slate and can do whatever I want?  I am not sure how many partions I need, how to configure/format/install to them etc.  Noob stuff...

Thanks so much!

---

### Post by teet on 2006-04-17
As far as I know you have to install windows first (unless you like major headaches!).  It doesn't like to share.

So, just make a 15-20 gb partition (bigger if you think you may install games or smaller if you just need office or something) from the windows installer screen and install windows to it.  Once windows boots up for the first time, reboot and put in your ubuntu cd and install that.

You may also want to make a 5-10 gb vfat (i.e. fat32) partition so that you can EASILY share files between the two (or just format the windows partition as fat32 instead of NTFS).

-teet

---

### Post by htinn on 2006-04-17
You'll want to read this:

[https://wiki.ubuntu.com/HowtoPartition](https://wiki.ubuntu.com/HowtoPartition)

---

### Post by babalou on 2006-04-17
[QUOTE=htinn]You'll want to read this:

[https://wiki.ubuntu.com/HowtoPartition](https://wiki.ubuntu.com/HowtoPartition)[/QUOTE]
since the purpose here is to install WinXP before Ubuntu, I'm not sure using the Ubuntu partitioner is the most straight forward approach. So I would rather agree with **teet **approach.

nice tutorial from Mehdi Hassanpour available here: [http://www.hezardastan.org/breezy_xp_dualboot/en/](http://www.hezardastan.org/breezy_xp_dualboot/en/)

yb

---

### Post by WATRD on 2006-04-17
Okay, thanks for the help!  I partioned the drive using the windows installer then finished up my windows install.  Then, using the partioner in Ubuntu, I set all the partitions to "Do not use" except the one I wanted it to install on. 

It did the rest beautifully and almost without input from me.  :)  I am successfully dual booting on my new drive now :)

So, next question, how can I change the default boot OS in grub?  I have tried to edit /boot/grub/menu.lst, but it tells me that I am not the owner and am not allowed to edit it.

I want to set it to boot to windows as the default, for now...

---

### Post by ds[de] on 2006-04-17
[QUOTE=WATRD]So, next question, how can I change the default boot OS in grub?  I have tried to edit /boot/grub/menu.lst, but it tells me that I am not the owner and am not allowed to edit it.[/QUOTE]


If you are in a terminal, type sudo gedit /boot/grub/menu.lst then enter your user password. Then you can edit the file (just change the value next to "Default" to whatever line is representing Windows in GRUB (starting with '0' I believe, but not sure about it).

Regards,
ds[de]

---

### Post by WATRD on 2006-04-18
Thank you very much for the reply.  That did the trick :)  I have 10 seconds to change it, otherwise it defaults to booting windows.

I have much to learn!

---

