---
title: "New installation"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by Wiredk on 2006-03-25
Heya, had some problems on windows XP, and seeing that I just got my ubuntu cds in the mail I decided to just use that instead.

Anyways, Here is my system info
I'm not sure on the motherboard, but I'm using the AGP version of the Geforce 6600, 1 gig of ddr ram, a amd 64bit processor, and two hard drives.

The issue I'm running into, is that the unbunto install just stops what its doing after "running the partitioner" and all I get is a line I can type in at the bottom.

Its probably that my partition is screwed up, or that its running nts or whatever the windowsxp file format is. 

Anyways, I would like to format my system - keeping in mind that I have a lot of files on the second hard drive I'd like to be able to use still, what file system format should I use? Also, is there a way to get the ubuntu install cd to format the drive I'm going to be setting this up on?

---

### Post by Pragmatist on 2006-03-26
Get yourself a copy of Knoppix here:
[http://www.linuxiso.org/](http://www.linuxiso.org/)

Knoppix is a LiveCD  This means that the OS is operating entirely off of the CD drive so you can use the tools in a complete Linux environment to work on your hard drive and make whatever changes you want.

After you run Knoppix open a terminal (it will probably be on the system tools or similar menu).  and type this:
```
su
```
Now type this:
```
ls /media
```
and look for your hard drive (it will be something like hda or hdb or sda or sdb...etc..etc..)  If, for example, your hard drive is the first drive on your first IDE port it will be designated as /dev/hda  do this:
```
fdisk /dev/hda
```
Now print your partition table by typing:
```
p
```
Then write down the partition table and post it here and we'll help you.
To exit fdisk just type:
```
q
```

---

### Post by BoneKracker on 2006-03-27
Why not just use the Ubuntu LiveCD to do that (which he already has)?

I believe that is one of the two CD's that come in the shipped package (Install CD and Live CD).

---

### Post by Pragmatist on 2006-03-27
> Originally Posted by: **BoneKracker**
Why not just use the Ubuntu LiveCD to do that (which he already has)?

No reason.  That would be a perfectly reasonable suggestion.  In my limited experience, however, I recall some posts where it wasn't trivial to get root privileges using the Ubuntu LiveCD.  Also, as far as I understand it, the Ubuntu LiveCD isn't as powerful or robust as Knoppix.  Many people I know, including myself, have used Knoppix for years to troubleshoot hardware--it is known for that.  There are people who permanently use knoppix as their main system!  I doubt anybody is doing that with the Ubuntu LiveCD.  So that is why I encourage others to get Knoppix into their set of tools.

---

