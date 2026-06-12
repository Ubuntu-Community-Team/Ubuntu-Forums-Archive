---
title: "Softpedia. Ubuntu. Conflicting instructions on Ubuntu Studio"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Ludford on 2007-07-18
Well, Ive downloaded ubuntu studio and following this guide

[http://news.softpedia.com/news/How-to-Install-Ubuntu-Studio-54514.shtml](http://news.softpedia.com/news/How-to-Install-Ubuntu-Studio-54514.shtml)

I inserted a DVD - R into my drive, but the iso image will not burn to it, It keeps saying burn failed.

the Ubuntu site says to burn it onto a CD

Who do I belive? and isn't a CD to small anyway? being 700mb when the ubuntu studio iso is over 800mb

---

### Post by loserboy on 2007-07-18
yea it needs to be a DVD...  are you sure that your DVDRs  and your drive works

---

### Post by Ludford on 2007-07-18
yes I am using, Philips DVD-R, 4.7gb 1-16x.


Although I get the same error when trying to burn movie files to the -Rs (like avi's)

is that normal, (things burn to +Rs fine)

---

### Post by MetalMusicAddict on 2007-07-18
Are you using Windows or linux to burn the image?

---

### Post by Ludford on 2007-07-18
Windows, using nero

I then go to "burn image to disk"

[IMG]http://img.photobucket.com/albums/v669/matts_skinz/error.jpg[/IMG]

---

### Post by MetalMusicAddict on 2007-07-18
Everyone who has this issue is using Nero. Theres a setting to fix this somewhere but its been so long I forgot where.

DVDdecrypter will burn it no issue.

---

### Post by Ludford on 2007-07-18
```
 DeviceIOControl(FSCTL_LOCK_VOLUME) Failed!
Device: [0:0:0]_NEC DVD_RW ND-3530a 1.80 (D:) (ATA)
Unable to lock volume for exclusive access.
Reason: Access is Denied 
```

thats what DVDdecrypter gives me, and

[IMG]http://img.photobucket.com/albums/v669/matts_skinz/error2.jpg[/IMG]

Could it be that it is called "CD Drive (D: ) in my computer when it is in fact a DVD drive?

EDIT: It's called "DVD-RW Drive (D: ) " when a cd isn't in it

---

### Post by loserboy on 2007-07-18
any chance you're using memorex discs, because i've seen a few posts recently about memorex disc problems

---

### Post by Ludford on 2007-07-18
NVM, I'm using a different disk now, "Verbatim" instead of "phillips"

is there a guide out there for installing duel boot ubuntu studio?

becuase I couldn't find the option "Resize IDE1 master, partition #1 (hda1) and use free space").

and the sofpedia says to use "guided- entire disk", but I only want to duel boot.

and the manual duel boot instructions here [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot), arn't very beginner friendly.

EDIT: where do I get the program that this guy uses at the start of this tutorial [http://www.chaohan.com/node/97](http://www.chaohan.com/node/97) ?

Its called system rescue CD, and it has that partition editor on it.

---

### Post by loserboy on 2007-07-18
[http://ubustu.com/](http://ubustu.com/)

look over that page for a howto using official DVD, they also have some other good stuff too

---

### Post by Ludford on 2007-07-18
Thanks but it seems that the guide isn't about dual booting since in the video its never shown that windows can still be booted.

---

### Post by MetalMusicAddict on 2007-07-18
Any guide that uses Ubuntu/Windows works.

---

### Post by Ludford on 2007-07-18
I'm just cautious about it because it doesn't show the screen where he chooses which OS to boot.

---

### Post by loserboy on 2007-07-18
sorry I thought you were looking for a howto on the non-graphical installer.

the dual boot part is set up by GRUB, so as long as you don't overwrite your windows partitions it will automatically add a boot option for windows.

I assumed that you had used Ubuntu before and were familiar with that

---

### Post by Ludford on 2007-07-18
I ran ubuntu on my laptop for about a week, but removed it becuase of various bugs. I'm hoping ubuntu studio is better.

(I didn't have a dual boot, I ran ubuntu as my only OS)

---

### Post by MetalMusicAddict on 2007-07-18
> **Ludford said:**
> I ran ubuntu on my laptop for about a week, but removed it becuase of various bugs. I'm hoping ubuntu studio is better.

(I didn't have a dual boot, I ran ubuntu as my only OS)

If you had problems with Ubuntu will have problems with Ubuntu Studio as they have the exact base.

---

