---
title: "PowerMac G4 500MHz (AGP) will not boot on CD"
date: 2007-02-21
forum: Apple PPC Users
---

### Post by crewmark on 2007-02-21
I was going to get a new box and install linux and then I found ubuntu. So I installed another drive into my PPC (PowerMac G4 500MHz AGP 512Mb RAM OS X 10.3.9) and downloaded both the ubuntu-6.10-desktop-powerpc.iso & kubuntu-6.10-desktop-powerpc.iso, followed the instructions and burned each onto a cd. Tried both... one after another on start-up but the cd wasn't recognised. The CD is recognised when inserted under OS X.
Am I missing something? I have gone through the forum, have tried resetting the PRAM and the Power Management... but nothing.
Any ideas?:confused:

---

### Post by maxamillion on 2007-02-21
when it is booting hold down the "opt" key and that should bring you to a page with icons on it allowing you to select what boot device and if there is a linux cd in there that is valid and has been burnt correctly it will shot a little picture of a cd with a penguin sitting next to it ... click it and you should be good.

---

### Post by Tommy on 2007-02-21
> **crewmark said:**
> The CD is recognised when inserted under OS X.


What do you see when you insert the CD under OS X? If you see only one file, then it didn't burn as an image. If you see a number of directories and files, then look inside to see if you can open some of the text files. 

Ideally you would also check the MD5SUM of the disk to verify that it burned properly, but that's harder (until you are able to boot it, and then verifying the disk is a menu option).

I have had good luck using the Mac OS X disk utility to burn an .iso file, but others have found (in other threads here) sometimes there is a hardware issue to overcome, too.

---

### Post by crewmark on 2007-02-21
Tried starting with option down and still nothing.

I can browse the CDs whilst in OS X and can read the text files.

I burned the CDs on my PB1.67GHz running 10.4.8 do you think that could be the problem?

---

### Post by oswaldkelso on 2007-02-23
If I remember correctly you must not open the iso with the finder  before you burn as osx can corrupt it . I had some trouble on a similar G4. 

Most problems are from dodgy burns. I alway drag any down loaded iso's into the left hand panel of disk utility (in osx) high light and select burn. never open the iso first. 

Holding down the option key will give you all boot able media inc osx partions, linux partitions, cd and dvd's, firewire etc.

Holding down the C key will boot from cd ( if the cd is ok) hope it helps

On older machines many people have better success with the Alternative cd.

---

### Post by crewmark on 2007-02-23
Thanks for all your advice guys. I ended up downloading the DVD version and trying that but again nothing.... I changed keyboards, because, you never know, and voila!
Idiot :lolflag:

---

