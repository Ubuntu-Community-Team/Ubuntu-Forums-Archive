---
title: "Man..so close...disk full???"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by gigaferz on 2006-07-21
i have a 120gb disk..70 for windows and 40 for linux...
IOn the linux yI decided to make the swap and root partitions..2 and 3 gb 
..I installed downloaded and executed automatix...after dowloading a bunch of things..I got a message saying the disk is 99% full...Do I need to esize the root partition..or what should I do?????

---

### Post by nalmeth on 2006-07-21
You left 40 for linux but only used 5 total?

Yes, you could resize the HD, do you have your install disk? May want to backup any important files if you haven't already.

Boot up the disk, hit ALT-F2

gksudo gparted

---

### Post by mmcmonster on 2006-07-21
My linux partition scheme is:
10 GB for root (I've never gone beyond 8GB on Ubuntu),
1 GB for swap (It's supposed to be double your physical memory)
rest for /home/

This way you don't lose your personal data (in /home) if you need to do a clean install of any linux distribution.

---

### Post by gigaferz on 2006-07-21
Ohh..Ok I get It...I do not remember where I saw that at least 1gb for root and 256mb for swap...that is why I have only 3gb for root...the rest I left it for home...Thank you..i will resize it ..Is there any difference if use the gnome partition editor, or is it better the command line?

---

### Post by avtolle on 2006-07-21
if you need a little breathing space, run from terminal:

"sudo apt-get clean" (obviously without the quotation marks) this will give you some elbow room, just in case you need it before resizing your partitions. Good luck.

---

### Post by Phen0m24 on 2006-07-22
> **avtolle said:**
> if you need a little breathing space, run from terminal:

"sudo apt-get clean" (obviously without the quotation marks) this will give you some elbow room, just in case you need it before resizing your partitions. Good luck.

I followed a similar path:

On a 60 GB HD I have 40 GB for the XP partition, 5 GB for the root, 1 GB for the swap, and the rest for Home.

Please forgive my ignorance, (noob here) but how do you save in different spots?  That one 5 gb partition reached 95% today and I've not even used Ubuntu for 24 hours yet!  (Was up until 3 AM this morning installing it)  Automatix filled up a big chunk of the space, and then I was trying to download something that I thought was saving to Home...

---

### Post by gigaferz on 2006-07-22
Hello...
Well since I could boot from ubuntu..I tried windows...and It was not working..it said file system unknown, partition type 0x7
save default make active chain loader x 1

since i LEFT the live cd somewhere else..I tried reinstalling windows with  some recovery discs That I made  with an HP  utility.

When I thought I was ready to boot from windows.. disk error no sytem file..
so ubuntu was unreachable...

Well I got the live cd again..formatted and repartiotioned the hard drive..

And now..
The LIve cd Freezes when it reaches 71%..... I have tried 3 times already..and  failed...It even failed when I selected the erase hda1 and install...

Now I was looking on the net for some info,,when Ubuntu live..just stopped working!!!..AHHH

So far Its been working as usual...I ts been 2 hours...so Ill attemp to install ubuntu again..

OK.. So what happened with the Automatix Thing!!!

What Is the recomended size for root????..right now im going 13gb...is that enough???

---

### Post by gigaferz on 2006-07-24
hey phen0m

You fixed your problem already??

Did you reinstall??

I was reading around...and root (/) need about 10 GB...

---

### Post by Phen0m24 on 2006-07-31
Yeah, I just broke down and re-installed.

---

