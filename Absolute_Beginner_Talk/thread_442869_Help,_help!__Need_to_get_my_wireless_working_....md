---
title: "Help, help!  Need to get my wireless working ..."
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by salea on 2007-05-13
Okay, hi.  I realize that there are probably plenty of topics about this in the forums, and the most relevant ones that I've found through googling and wikiing, I've already tried.  I am an owner of a Compaq Presario v3000.


What's worse, my wireless networking card, which is ... well, I can't remove it without opening my laptop, is woefully, a bcm4311.

I hate it.  A lot.  Anyway.  I installed Ndiswrapper, after much frustration, as well as the linux kernel header files for my kernel version, blacklisted bcm43xx, and used the bcwl5 driver for it, but sadly, it doesn't work.

The reference source about Ndiswrapper pointed me to the driver list for the 4311, which is the win32 driver, but I'm not sure how to get it.

What's more, the actual FAQ for installing things on bcm4311 at ubuntu asks me to use the command:

sudo depmod -a

Which, after a lengthy amount of time, gives me the return message:

Bus Error

So, my problem is ... what's a 'bus error' ... what can I do to get my network card going ...


Annnnnnd ...

I have another problem.  I installed ubuntu by killing my Windows Recovery Partition so.... yeah.  Didn't copy it to discs, because I SUCK, and didn't know I could.  Right.  In any case, I have a few ... problems here. 
The system file, under C:\WINDOWS\SYSTEM32\CONFIG\SYSTEM ... WELL, it's corrupted.  For whatever reason.  Annnnd, I'm more or less f*cked.  As far as Windows goes.

 The solution is to get a Windows XP set up disk, the one coded for my computer, which I've yet to order, but will.

Problem is, long ago, I set a password at boot up.  As soon as I enter it in, it takes me straight to the GRUB operating system chooser thing.  So, I can't remove the password.  What I'm afraid of is ... how in the world will, when I get the set up disk, I be able to use it to ... well, fix that file.

Is there a way I can fix it using ubuntu?

Ah, btw: 

I am using ubuntu 6.06, Dapper.  I've installed Ndiswrapper, I have the bcmwl5 driver installed currently.

Solutions?  I use a bcm4311 Broadcom wireless card.  God, HELP ME.


Thanks in advance!

---

### Post by wormser on 2007-05-13
[This guy]("http://cro.alienpants.com/index.php/2007/05/05/getting-ubuntu-running-on-my-compaq-f500/") says that [this worked]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29") on his bcm4311

Good luck :)

---

### Post by salea on 2007-05-15
When I use depmod -a, after a brief time, I get the line:

Bus error

... why?

---

### Post by salea on 2007-05-16
*bump*

---

### Post by esoterica on 2007-05-16
I've certainly heard of a lot of people having problems with Broadcom wireless cards, enough to make me glad I don't have one, or if I did I'd spend the couple dollars to buy a different wireless card and pull it out and dump it in the trash.

I have a "Restricted Driver" that Ubuntu installed by default for my own Intel Pro wireless card built into my laptop. I've found Open Source drivers for it on Source Forge that I'd like to install instead but I'm still trying to figure out how to remove the existing drivers and replace them with the new ones in Linux, it's been so long that I don't remember how, so I can't help you with that part yet.

While I was searching for drivers for my own card though (which is working, another reason why I'm hesitant to mess with it) I did run across a lot of links referencing your specific card, many were pointing to these drivers for that card to work under Linux...

[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

That website has a link to the documentation for your specific card on the Ubuntu web site that points to here...

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Some of the sites pointing to those drivers had rather discouraging comments about them like so...

>  
These reverse-engineered drivers support a range of Broadcom based wireless cards. These drivers are in a state of high development, and support is only added because of demand.  If it doesn't work, I wouldn't be too surprised.


---

