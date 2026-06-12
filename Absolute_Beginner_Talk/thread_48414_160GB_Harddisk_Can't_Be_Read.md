---
title: "160GB Harddisk Can't Be Read"
date: 2005-07-12
forum: Absolute Beginner Talk
---

### Post by anwarlorenzo on 2005-07-12
Hi! I've tested the other day the Knoppix 3.9 release and everything was detected and configured just fine. But the one thing that wasn't working was my 160gb hard drive.

It was formatted using seagate's disk manager to NTFS that came with ultimate boot cd ([http://ubcd.sourceforge.net/)](http://ubcd.sourceforge.net/)). But since my old motherboard (GA-BX2000) doesn't support drives higher than 136gb (i think), it was formatted at 136gb.

whenever I double click the desktop icon for the 160gb drive it says something about an invalid filesystem or soemthing like that. I can't mount manually. My other NTFS drives are read without problems.

I'm planning on ditching XP and migrating to Ubuntu soon but I can't until my 160gb drive can be read. Please help.

Thanks in advance! :)

---

### Post by aysiu on 2005-07-12
I'm confused. Are you using Knoppix or Ubuntu?
Just so you know, Linux can successfully read from NTFS, but it can't write to NTFS consistently.

Maybe this will help?

[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by maruchan on 2005-07-12
Well, this may or may not help, but my 160GB NTFS drive is working great :)

---

### Post by anwarlorenzo on 2005-07-13
Hi again :)

What I meant was I used Knoppix to "test drive" linux and see if my hardware are all  working in it before I switch to Ubuntu.

All worked except for my 160GB drive which was detected and maybe autoconfigured  already but whenever I try to access it, something like "invalid filesystem".

The drive was formatted using Seagate's Disc Wizard to NTFS and to 136GB only since my motherboard only supports that maximum capacity. My motherboard is a Gigabyte GA-BX2000 btw.

---

### Post by aysiu on 2005-07-13
Knoppix is a great way to "test drive" Linux, but if you're thinking of installing Ubuntu, it may be better to "test drive" with a Ubuntu live CD, as that will give you a better sense of how Ubuntu behaves and what hardware it recognizes.

That said, is there any reason in particular the hard drive *needs* to be formatted as NTFS? I understand NTFS is the native filesystem for Windows XP, but an external hard drive can easily be FAT32 (my 160 GB Lacie is FAT32).

---

### Post by anwarlorenzo on 2005-07-13
[QUOTE=aysiu]Knoppix is a great way to "test drive" Linux, but if you're thinking of installing Ubuntu, it may be better to "test drive" with a Ubuntu live CD, as that will give you a better sense of how Ubuntu behaves and what hardware it recognizes.

That said, is there any reason in particular the hard drive *needs* to be formatted as NTFS? I understand NTFS is the native filesystem for Windows XP, but an external hard drive can easily be FAT32 (my 160 GB Lacie is FAT32).[/QUOTE]


I guess there's no particular reason. I just thought that since I'm going to use XP (I have no plans of using Linux yet when I bought the drive) then I'd go ahead and format it to NTFS.

What I'm wondering is, why can't it be mounted properly? Could the Ubuntu live CD do it successfully?

Oh btw, could I change the partition to FAT32 or maybe to the filesystem Ubuntu uses without loosing my data?

Thanks again! :)

---

### Post by aysiu on 2005-07-13
To be honest, I'm kind of surprised. Knoppix is pretty good about getting things right. Even though Linux can mount NTFS as read-only, it's still usually readable.

It's highly unlikely that you can reformat your hard drive while keeping the data on it. You'd have to back up the data, reformat it to FAT32, then put the data back on.

Do you want your hard drive to be read-only? Because even if the hard drive mounts properly, Linux will not be able to successfully write to NTFS.

I still think your best bet is to try a live Ubuntu CD.

---

### Post by flak9 on 2005-07-13
I would grab the ubuntu livecd and test it.  When I tested several systems using Knoppix and the Ubuntu livecd, the ubuntu disc found and setup more hardware than the Knoppix disc.  It is easy and worth a shot!

---

### Post by anwarlorenzo on 2005-07-13
Ok will do. I'll post again for updates. Thanks a lot guys :D

---

