---
title: "need help installing Ubuntu for the first time !"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by pushkal on 2007-10-22
Hi !
I am installing ubuntu beside XP for the first time and i cant figure out what a linux partition is (ext3 ,ext2..), whats the difference  bw these two ?
and other things like 
1.cant swap space be there on the installation drive itself or a partition is neccessary?
2.can swap space be used for storing other files like documents etc..?
3.whats '/home' and all other tech stuff?? :confused:
i have a 160 gb hdd pre-partitioned into 20(has XP),20(for linux),60(docs..),60(docs,games..) &
amd athlon X2 processor (this means i have to install the ubuntu 64 bit edition.. right?? or will a 32 bit edition work fine??)
i want to know everything before i proceed..
i am prepared to study more about linux..and ubuntu and everything
related to it which clears my doubts..
:)
thanx for ur time !

---

### Post by Sef on 2007-10-22
Read [Psychocats Installing]("http://psychocats.net/ubuntu/installing").

> what a linux partition is (ext3 ,ext2..), whats the difference bw these two ?

They are file systems.  [Ext3]("http://en.wikipedia.org/wiki/Ext3") is the default file system in Ubuntu.  Just go with it now.

> 1.cant swap space be there on the installation drive itself or a partition is neccessary?

How much ram do you have?  If you have a gb or more, swap is not that necessary, unless you are into gaming or editing movies. 

> 2.can swap space be used for storing other files like documents etc..?

No, it can't.

> 3.whats '/home' and all other tech stuff?? 

Home is where your files are saved.

Describe other tech stuff in detail.

> amd athlon X2 processor (this means i have to install the ubuntu 64 bit edition.. right?? or will a 32 bit edition work fine??)

The 32-bit will work fine.  Get that and use it at first.  After a while, when you feel comfortable with it, then you can install a 64-bit.   There are some tricky technical things about 64-bit that don't make it newbie friendly.




---

### Post by realvz on 2007-10-22
Go for it...delete WinXP and let Ubuntu have the whole disk...

thats what i did...

Just kidding..

follow this tutorial...and have fun

[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

WELCOME TO UBUNTU

---

### Post by Cheat King on 2007-10-22
I uninstalled Vista and did it. :P I got Vista for free anyway... ;)

---

### Post by slira on 2007-10-22
Hi there
I have XP and Ubuntu runing (dual boot) in my laptop; it works fine; if you have any specific problems, just post.
I migrated all my work to ubuntu; now, I'm just using XP for heavy/complex powerpoint presentations that do not run properly on OpenOffice... but they will, with some time and patience; all the rest is in Ubuntu.
Welcome to UBUNTU! :) have fun
slira

---

### Post by pushkal on 2007-10-22
thanks for ur reply..
i have 1GB of ram  and i like to play games as well..think i wud make a swap partition instead..
and about the other tech stuff..
i dunno 
what /dev/sda1,/dev/sda5,sda6,sda7 mean and 
what is a mount point..like /media/sda 1,sda5,sda6,sda7 
(also where did sda2,3,4 go?? (am i a complete noob ?..ohh yess..i am))
also when i put in the cd and choose start or install ubuntu..
an error pops up saying X sever coundnt be started and when i look into the details it says 
Fatal server error: no screens found
but when i run it in safe graphics mode it works fine..
maybe my laptop screen is bugging it ..

---

### Post by pushkal on 2007-10-22
thanks for ur reply..
i have 1GB of ram  and i like to play games as well..think i wud make a swap partition instead..will a 2 GB partition do well enough ??
and about the other tech stuff..
i dunno 
what /dev/sda1,/dev/sda5,sda6,sda7 mean and 
what is a mount point..like /media/sda 1,sda5,sda6,sda7 
(also where did sda2,3,4 go?? (am i a complete noob ?..ohh yess..i am))
also when i put in the cd and choose start or install ubuntu..
an error pops up saying X sever coundnt be started and when i look into the details it says 
Fatal server error: no screens found
but when i run it in safe graphics mode it works fine..
maybe my laptop screen is bugging it ..
i hope when i install it from the safe graphics mode and boot it ...it wont say "no screens found buddy..\\:D/ format the drive"..
thanks 4 all the help !

---

### Post by slira on 2007-10-22
> **pushkal said:**
> 
i have 1GB of ram  and i like to play games as well..think i wud make a swap partition instead..

make a swap partition 1,5x your RAM - should work fine

> **pushkal said:**
> 
what /dev/sda1,/dev/sda5,sda6,sda7 mean and 

that's the way linux calls your drives; hd and sd (internal or external disks); a,b (first, second, etc disks); 1,2,3, (your partitions)

> **pushkal said:**
> 
what is a mount point..like /media/sda 1,sda5,sda6,sda7 

that's where your drives are mounted; if they are not, you will not have access; your drives should be mounted after installation;
(if not, you can use the command 
[FONT="Courier New"]sudo mount -a[/FONT] in a shell, for example for mounting all your externals (usb pens, etc.); but this is not for now: after you have your ubuntu running you will ask for some help concerning your fstab)

> **pushkal said:**
> 
also when i put in the cd and choose start or install ubuntu..
an error pops up saying X sever coundnt be started and when i look into the details it says 
Fatal server error: no screens found
but when i run it in safe graphics mode it works fine..
maybe my laptop screen is bugging it ..
what graphic card do you have?

Best
slira

---

### Post by pushkal on 2007-10-22
Nvidia Geforce 7000 M..i also found out that when i run ubuntu in safe graphics mode it shows somethin like Restricted drivers and displays NVIDIA accelerated graphics driver(latest cards) Not in use ..will i have to download the drivers ??
and u left the question-- where did sda2,3,4 go?? (in my laptop it only shows /media/sda 1,sda5,sda6,sda7)..
about the mount point..to install ubuntu what should i keep my mount point as ??

Thanks !

---

### Post by slira on 2007-10-22
> **pushkal said:**
> Nvidia Geforce 7000 M..i also found out that when i run ubuntu in safe graphics mode it shows somethin like Restricted drivers and displays NVIDIA accelerated graphics driver(latest cards) Not in use ..will i have to download the drivers ??
and u left the question-- where did sda2,3,4 go?? (in my laptop it only shows /media/sda 1,sda5,sda6,sda7)..
about the mount point..to install ubuntu what should i keep my mount point as ??

Thanks !

Hmmm, about the drivers, probably the live cd doesn't have the required drivers for that card. what version of Ubuntu are you installing? Anyway, if it doesn't have it, you will have to download them as soon as you install the system (easy stuff). Meanwhile, you can use the generic ones.

Also, since kernel 6.6.22 hd isn't used anymore, and everything is sd. That means sda will be your internal hard drive. As for partitions,

I am guessing a little,a according to your description, but I would say 1 is your windows partition, then 2 and 3 are your docs/games ones (in windows therefore NTFS file system). 4 is usually extended (it can have logical "under" it). Then 5, 6 and 7 I am not really sure. 5 is probably linux, and I have no idea about 6 or 7 since you didn't specify. 

Let me tell you that info was for your kernel being 2.6.22 or superior. IF you have an older one (2.6.20 for example) I don't know why it is doing that. to check your kernel, type
[FONT="Courier New"]uname -r[/FONT]
in a command line (applications --> command line in the graphic environment) to know your kernel.

Hope it helps,

Slira

---

