---
title: "Can ubuntu rescue files from Windows XP?"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by MartyNg on 2006-09-17
My sister has botched up her Windows XP machine. I'm pretty good with Windows troubleshooting, but after several hours of not being able to do anything, even with the Windows Recovery Console, I got to thinking about Ubuntu. I've only tried Ubuntu a few times. Perhaps it could help me save some files. (It's a drive to my sister's house, so I didn't want to drive there to find out that I couldn't recover anything for her) Hopefully you guys have some advice..

Could I simply boot into Ubuntu live CD, then burn the "My Documents" folders from the Windows parition to a CD, then reinstall Windows and copy the files back? Or does the Ubuntu Live CD have to be in a CD drive the whole time (she only has one drive)? She pretty much just needs the files in the "My Documents" folders for several users.

Thanks for any advice!

---

### Post by aysiu on 2006-09-17
Yes, you can do this with Ubuntu, but Ubuntu is not *designed* as a rescue disk.

Knoppix (which is designed as a recovery CD) is much better suited to the task.

If you don't have a Knoppix CD, though, it still can be done.

Boot up the Ubuntu live CD.

Open a terminal. Paste in this command: ```
sudo fdisk -l
``` It'll list the partitions and their types. Let's just say, for the sake of this example, it's /dev/hda1 of NTFS filesystem type. ```
sudo mkdir /media/recovery
sudo mount -t ntfs /dev/hda1 /media/recovery -o nls=utf8,umask=0222
``` Then go to the desktop and get those files off!

---

### Post by jordanmthomas on 2006-09-17
The CD has to be in the whole time.  You could use a USB drive though.
(or...yucky as it may be...you could e-mail them and retrieve them later)

---

### Post by MartyNg on 2006-09-17
I have heard of that. I'll look into that. In the meantime, is it even worth trying Ubuntu, or should I go right to Knoppix?

---

### Post by aysiu on 2006-09-17
> **MartyNg said:**
> I have heard of that. I'll look into that. In the meantime, is it even worth trying Ubuntu, or should I go right to Knoppix?
If you have Knoppix, use it.

[quote=jordanmthomas]The CD has to be in the whole time. You could use a USB drive though.
(or...yucky as it may be...you could e-mail them and retrieve them later)[/quote] Good point. If you have two CD-ROM drives, though, you could burn it on one while using the other to run the live session.

---

### Post by bulldog on 2006-09-17
Rescue files with the live cd is certainly possible but as you stated,the cd must be in the player.

You can buy an extra player for a few bucks.
Or install Ubuntu on the hdd.

Options enough,you can pick one.

---

### Post by xpod on 2006-09-17
> The CD has to be in the whole time. You could use a USB drive though.
(or...yucky as it may be...you could e-mail them and retrieve them later)
Reply With Quote

Had to do that with a reinstall of mum in laws xp last week when i realised i did`nt have no place to put all her photo`s......yucky,like you say:(

---

### Post by adakadavule on 2006-09-28
hey heres da deal! simple it is! goto [www.puppylinux.org](www.puppylinux.org) n gedda puppylinux iso-75 megs i guess,burn to cd,goto sisters house,boot remove cd n rescue.Though i luv ubuntu,this is d best fr rescue.U c its small,so it loads entirely to ram n even works with old systems,so thats how u do it,i guess im  late,but hope it helps u in the future,all the best.

---

### Post by GreenHawkIA on 2006-09-28
Another option to Puppy (which is great) is Damn Small Linux, which will also load completely into memory so you can eject the CD.  You must have at least 128 MB RAM for this to work.  More info at [www.damnsmalllinux.org](www.damnsmalllinux.org).
Best!

---

