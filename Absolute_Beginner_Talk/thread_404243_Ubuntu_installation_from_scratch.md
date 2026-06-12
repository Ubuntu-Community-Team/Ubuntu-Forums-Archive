---
title: "Ubuntu installation from scratch"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by Gael33 on 2007-04-08
I'm the baby of the list ... only joined 30 mins ago and have absolutely no experience with Linux at all. 
Okay, my question is; I have downloaded Ubuntu 7.04 and I want to install it on my old machine to gain some experience before taking that giant leap into the unknown and moving away from Microsoft. At present my old machine has MS-Millennium OS, 550 pentium 2 processor, 1 GB memory and a 20 GB HDD.
The big questions are; Do I have to format the HDD ... if yes, FAT32 or NTFS or do I just leave it blank? Do I need a startup disk? Do I have to change any setting other than the boot settings?
As I've never done this before I will be eternally grateful for any tips that I receive.

Thanks in advance,
Gael.

---

### Post by Rui Pais on 2007-04-08
> **Gael33 said:**
> I'm the baby of the list ... only joined 30 mins ago and have absolutely no experience with Linux at all. 
Okay, my question is; I have downloaded Ubuntu 7.04 and I want to install it on my old machine to gain some experience before taking that giant leap into the unknown and moving away from Microsoft. At present my old machine has MS-Millennium OS, 550 pentium 2 processor, 1 GB memory and a 20 GB HDD.
The big questions are; Do I have to format the HDD ... if yes, FAT32 or NTFS or do I just leave it blank? Do I need a startup disk? Do I have to change any setting other than the boot settings?
As I've never done this before I will be eternally grateful for any tips that I receive.

Thanks in advance,
Gael.

Hi, welcome to forum and Ubuntu.

Linux don't use fat32 or ntfs.
Just burn the iso image on a cd a boot from it.
The installer with present you with several option to deal with how to format/partition your hd.

You can see a preview of what will look the install process [here]("http://www.psychocats.net/ubuntu/installing").

Good luck.

---

### Post by Gina on 2007-04-08
Hi Gael :) Welcome to the forum :):)  And to Ubuntu - I'm a complete convert to Ubuntu/Linux :lol:

Take the ISO file you downloaded and burn it to CD as image (not data).  This will give you what's called a "live CD".  You can boot from this and run Ubuntu immediately and see if you have any problems - it will not touch your HD.  If you like it you can install it on HD with or without having it dual-boot with Windows.  As long as your Windows system doesn't take more than say three-quarters of the HD you'll have room for Ubuntu.  You will need to defrag Windows and turn off any unmoveable files such as swap or hibernate so that all the Windows files aree at the beginning - leaving space at the end to reclaim for Ubuntu.  You will probably need to defrag several times.  Then you can resize the partition containing Windows and create Linux partitions in the space you've freed up.  Run Install in Ubuntu to install it to HD.  This version of Ubuntu will also let you import your settings and Documents, Favorites etc. from Windows into Ubuntu if you would like (but only if you choose to keep Windows when installing).

Alternatively, if you no longer want Windows on that machine and don't want any data on it, you can tell Ubuntu to just use the whole drive to install onto.  It will wipe Windows and everything, create it's partitions and install straight off.  Just a few easy questions to answer.

---

### Post by mikewhatever on 2007-04-08
I support the advice of trying Ubuntu from the live cd. This will make sure your hardware is supported, and, that you get a feeling of what this new OS is like. You can do most of the stuff, including getting on line, creating documents, saving to removable media etc. The biggest drawback, Ubuntu is slow from the live cd, but, after a few days or hours, you might decide you like it enough to install. Here is a guide
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

### Post by flossgeek on 2007-04-08
Also Feisty is still beta, you shouldnt really be using this version unless you are a tester. I would download dapper drake 6.06LTS or edgy eft 6.10.

---

### Post by laidback on 2007-04-08
I agree with flossgeek, go with 6.06LTS as a starter. Use the Live CD version too, it's good advice. The great thing about Ubuntu (and Linux in general) is that you can move onto the other versions later at no cost to yourself (except download time). Alternatively order CD's from Ubuntu, 6.06 is completely free including postage, I believe that there is a small charge for others.  I use 6.06LTS as my main distro but have 6.10 and others for fun.

Welcome to Ubuntu.

---

### Post by Gael33 on 2007-04-10
Thanks for all the advice guys ... I've downloaded version 6.10 and I'll burn the image to disk and take it from there. I'll run it from disk as suggested to start with and perhaps later I'll install the program on to my PC. Anyway, wish me luck and in due course I'll let you know how I went on (LOL).
Thanks again,
Gael.

---

### Post by akl604 on 2007-04-14
Hello, I am also brand new here and I am sneaking into this thread since my problem is almost identical. I have a spare 7 year old Toshiba laptop with Win Me and a 500 MHz Celeron. I would like to try Linux on it, and it's fine to remove Windows from it.

I have successfully downloaded and burnt to CD Ubuntu 6.10, but the installation goes only as far as the language selection. Once I select English, the laptop freezes forever. I have tried many times with a similar result (sometimes the laptop freezes before reaching the language selection).

I have also tried 6.06.1 with similar problems (actually, the laptop freezes before even I get to the language selection). Additionally,  6.06.1 gives me error screens (see image).

Any ideas what I could be doing wrong?

---

### Post by flossgeek on 2007-04-15
How much ram does your Toshiba have? The screenshot you have posted is nothing to worry about usually, that sometimes appears when running a live disc.

---

### Post by akl604 on 2007-04-15
It has 192 MB RAM.

---

### Post by igknighted on 2007-04-15
You need 256mb ram to install from the liveCD.  Please download and install from the alternate install CD... it is just the installer so it doesn't load the whole OS.  Also, you might want to consider Xubuntu or Fluxbuntu with those specs.  Gnome will run really slowly, so you would get more responsiveness with the other two.

---

### Post by akl604 on 2007-04-15
That explains it! Thank you for the help; I might reappear in another thread with more questions!

---

