---
title: "Ack!  Can't install Ubuntu!"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by jaymel on 2007-12-14
Help!  I'm trying to install Ubuntu for the first time, and am wanting to set it up with a dual boot w/WinXP.  When I try the guided mode for partitioning the HD, I get this error:

An error occurred while writing the changes to the storage devices.

The resize operation is aborted.

What am I doing wrong?  All I did was click install, answer the location/language questions, move the slider on guided mode to a smaller partition size (+/- 20GB), and I got that error after I got the warning message that changes cannot be undone.

If it matters, I also just formatted the HD to clear space.  I've installed basic drivers and WinXP.

Help!  I'm so excited to run this outside of Live mode!

---

### Post by thelatinist on 2007-12-14
Are you by any chance trying to dual-boot with Vista?  I understand Vista doesn't play well with other partitioners, so it may be necessary to free up space using Vista's partitioner before you try to install Ubuntu.

---

### Post by jaymel on 2007-12-14
I'm on XP Home... and have a freshly formatted 80 GB HD

---

### Post by Tyke91 on 2007-12-14
try a manual format

Go to the "manual" selection and set up your hard drive to look like this


Windows (however big you want it to be. make sure NOT TO FORMAT THIS PARTITION)

/  (this is the root partition,  it should be 10-30 gb... if you plan to install alot of programs, go with a larger root partition)

/home (it's a good idea to have a separate home partition in case you want to re install. This should be your biggest partition)

swap (should be approximately half the size of your ram and generally no bigger than 2 GB)

---

### Post by jaymel on 2007-12-14
OK, I apologize for my ignorance... but I am a little confused now I am in the manual mode.  Mine currently looks like this:
[U]
Device          Type   Mount Point   Size          Used[/U]
/dev sda
    /dev sda1  ntfs  /media/sda1  79990 MB  3500 MB
    free space                            8 MB

What should I do to change this?  What should it look like?

Thanks for helping a total noob! :)

---

### Post by LinuxGuy1234 on 2007-12-14
> **jaymel said:**
> OK, I apologize for my ignorance... but I am a little confused now I am in the manual mode.  Mine currently looks like this:
[U]
Device          Type   Mount Point   Size          Used[/U]
/dev sda
    /dev sda1  ntfs  /media/sda1  79990 MB  3500 MB
    free space                            8 MB

What should I do to change this?  What should it look like?

Thanks for helping a total noob! :)

Resize Windows and then create 2 new partitions.
My choice is:
Windows: 20GB
Ubuntu: 50.1GB
Swap: the rest

---

### Post by thelatinist on 2007-12-14
> **LinuxGuy1234 said:**
> Resize Windows and then create 2 new partitions.
My choice is:
Windows: 20GB
Ubuntu: 50.1GB
Swap: the rest

I would suggest a couple of changes from LinuxGuy1234's suggestions:

Ubuntu doesn't need 50 GB.  15 GB or even 10 GB should be enough.  And 10 GB is far too much for a swap partition: 2x your total RAM seems to be standard.  Also, since you will be dual-booting, you will probably want a shared data partition accessible from both OSes. My recommendation:

20 GB Windows
48 GB Shared Data (NTFS-formatted)
10 GB Ubuntu (ext3-formatted)
~2 GB swap

Adjust to fit your needs, of course.

---

### Post by kajillin on 2007-12-14
u dont need ten gigs for your swap partition, only partition twice the amount of ram u have on your machine for swap.

i dont know but this is my setup

297 gb for root
4 gb for swap 
1 gb for boot (i know its way overdoing it but w/e)

And the guided partitioner sucks so always do it manually

Also are you using the liveCD or doing a text-based install

And for an extra backup measure u could put you home on a seperate partition aswell, just so you can save you personal files incase u need a re-install

---

### Post by jaymel on 2007-12-14
Ahh.. I don't know what happened but after the 3rd reboot or so it finally would let me install it!  I'm writing this from the safety and security of Ubuntu :guitar:

Thanks!  Now I'm sure I'll be back for more help in the next couple of days :)  I hope someday I'll be as tech-savvy as you all are! :)

---

### Post by Tyke91 on 2007-12-14
welcome to the ubuntu community :) in time, you will learn the operating system like the back of your hand (probably far better than you know window$ now)

---

### Post by thelatinist on 2007-12-15
Indeed, welcome!  Don't forget to mark this thread as [Solved] so people don't keep coming back to it. Happy Ubuntu-ing!

---

