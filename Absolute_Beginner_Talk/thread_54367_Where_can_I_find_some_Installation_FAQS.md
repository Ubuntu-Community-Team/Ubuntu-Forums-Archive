---
title: "Where can I find some Installation FAQS?"
date: 2005-08-04
forum: Absolute Beginner Talk
---

### Post by Muhammad on 2005-08-04
:(

---

### Post by GavinX on 2005-08-04
You need to check here : [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) and here [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

Cheers,
GavinX

---

### Post by Muhammad on 2005-08-04
[QUOTE=GavinX]You need to check here : [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) and here [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

Cheers,
GavinX[/QUOTE]
 Thanks for the link :)

But I didn't quite find what I was looking for... SO I guess I'll make my question more specific:

After I make the Partions(sp?), I have an 80GB HD, so I made three partions, 40/39/1 the first 2  are fat32, and the last is a swap drive,and I see the smilies, I hit continue, after a while, I recieve the messege:

BASE SYSTEM INSTALLATION ERROR

The debootstrap program existed with an error (return value 1) check /var/log/messeges or see virtual console 3 for details.

What does it mean, and how do I fix things? :(

---

### Post by GavinX on 2005-08-04
Question: the drive to which you are installing, does it have on any operations system? And if it doesn't, do you plan to put any other OS on it, especially Windows? Because if you're planning to, i would advise that you install Windows first then install Linux. I kinda suspect that the error message may have to do with the way the drive is partitioned, the two FAT partitions, with a SWAP partition may be confusing the installer. A possible solution is to allow Linux to automatically partition the drive if you don't plan to put any other OS on it. If you plan to put on another OS, you will have to choose 'expert installation' on the CD and create the partitions yourself. However, PLEASE NOTE, LINUX DOES NOT USE FAT PARTITIONS. IT USES ITS OWN PARTITIONS, E.G. EXT2, EXT3..... So when creating the partitions, do not create FAT32. that's for Windows.

---

### Post by Muhammad on 2005-08-04
I'm going to use EXT3 then, thanks for the reply. :)

EDIT: To answer your question, no I formatted both drives, and I'm not planning to install winXP again if this OS works well. ;)

---

### Post by GavinX on 2005-08-04
Then it may make sense to let Ubuntu do the partitioning for you. It makes life so much easier.

---

### Post by Muhammad on 2005-08-04
It does! But during the base system Installation at 70% I've recieved the following error:

UNABLE TO INSTALL THE SELECTED KERNEL

An error was returned while trying to install the kernel into system

Kernel package linux-386

 :-?

---

### Post by GavinX on 2005-08-04
did you do a default install? if that's the case, you may have to try another option. I'm not familiar with that error message.

---

### Post by Muhammad on 2005-08-04
How do I change the default install? And to what must I change it to? I didn't know you can actually change the way the installation goes...

---

### Post by GavinX on 2005-08-04
Yah, it can be changes. When you boot the cd, it should say something to the effect "for help press F1......" Don't remember what exactly it says. But follow what they ask for. Afterwards, it should show a menu with some options and one of them should be "for ways to boot this CD press F......" When you get to the options, look for one which says booting kernel 2.4. Follo those instructions and see what happens.

---

### Post by Muhammad on 2005-08-04
Ok thanks, I going to try it, you see I'm running the live CD version now so I could be able to access the internet, and find help. I'll be Back! :P

---

### Post by vimme on 2005-08-04
I have two HDs, 80gig and 160gig. I'm planning to install Ubuntu on the 80gig HD that is now partitioned to two pieces, 7gig for Windows (c:) and ~70gig(d:) for windows programs/games etc. Atm I have almost 60gig of free space on that D: drive...

Am I able to partition from D: drive, let's say 10gigs for Ubuntu + swap with the installer so that I won't lose current windows files? Or should I use PartitionMagic or something. I'd sure prefer using Ubuntu installer if possible, to get most out of the installing and getting to know my new OS better..

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=vimme]I have two HDs, 80gig and 160gig. I'm planning to install Ubuntu on the 80gig HD that is now partitioned to two pieces, 7gig for Windows (c:) and ~70gig(d:) for windows programs/games etc. Atm I have almost 60gig of free space on that D: drive...

Am I able to partition from D: drive, let's say 10gigs for Ubuntu + swap with the installer so that I won't lose current windows files? Or should I use PartitionMagic or something. I'd sure prefer using Ubuntu installer if possible, to get most out of the installing and getting to know my new OS better..[/QUOTE]

The ubuntu installer CAN do it. Partition magic can do it easier. Also parition magic can turn you main partition into fat32 so that Linux can read and write to your files.

---

### Post by vimme on 2005-08-04
Thanks for such a quick response. Think that I'll go with the installer then, I'm not looking for the easier way but most educative way to do it  :wink:

---

### Post by Muhammad on 2005-08-04
OK the installation went succesfully, and I'm using Ubuntu now :D
I pciked expert installation instead of the normal one and put Linux image386 instead of Linux386.

But how come I'm not an admin on my own computer, I don't rememeber being given the choice to become an admin or not... :mad: ?

---

### Post by Knome_fan on 2005-08-04
[QUOTE=Muhammad]
But how come I'm not an admin on my own computer, I don't rememeber given the choice to become an admin or not... :mad: ?[/QUOTE]

Simple, root isn't enabled by default on ubuntu. Instead ubuntu uses sudo.
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
This should explain it a little better than I can.

Have fun!  :grin:

---

### Post by GavinX on 2005-08-04
[QUOTE=Muhammad]But how come I'm not an admin on my own computer, I don't rememeber given the choice to become an admin or not... :mad: ?[/QUOTE]
In Ubuntu, to become admin, you use the 'sudo' command. it's a way to protect you and your system. I highly advise that you become very familiar with this [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) You will find lots of stuff to help and guide you there.

---

### Post by Muhammad on 2005-08-04
Thanks again Knome_fan and Gavin :) The guides did help me alot to figure out a few things, but I still have problems ](*,) 

The guide says that anything written in black boxes must be typed in the root terminal, yet I can't access the terminal because it asks me for a password which I still haven't figured out... :mad:

EDIT: Apperantly I misread, I should type the commands in Terminal not root Terminal XD

---

### Post by GavinX on 2005-08-04
Great. Just use the password which you use to log into the system.

---

### Post by Muhammad on 2005-08-04
When I typed "sudo passwd root" in terminal I recieved the following messege:

> muhammad is not in the sudoers file.  This incident will be reported.

Huh? What? :???:

---

### Post by Knome_fan on 2005-08-04
[QUOTE=Muhammad]When I typed "sudo passwd root" in terminal I recieved the following messege:



Huh? What? :???:[/QUOTE]
Strange. Is muhammad the original user you created when you installed ubuntu. Only this user will be added to the sudoers file.

---

### Post by Muhammad on 2005-08-04
Yes, I've made only one account and that was during the installation... :(

---

### Post by Muhammad on 2005-08-04
Do you think I should re-install the whole thing? :(

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Muhammad]Do you think I should re-install the whole thing? :([/QUOTE]

No. Just use the root terminal instead of sudo.

---

