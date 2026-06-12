---
title: "New User:Error readng boot CD"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Afrikprophet on 2007-06-17
Hello after sitting on the fence for months a crash on my Dell laptop drove me in the arms of ubuntu. I just made a cd of feisty fawn and loaded it in to my machine. The Ubuntu screen showed up witht he list of options (start and install etc) but when I select anything other than help the following words come across the top of the page 

 Loading isolinux: Disk error 01, ax = 4200, drive 82

and a dialog box saying 

I/O error
Error reading boot CD

and a button to reboot

I would reboot and the same thing would happen. 
Has anyone else encountered this problem, and if so how did you solve it? 
Ap

---

### Post by alienexplorers on 2007-06-17
Did you burn the disk at a low speed such as 4x?
You could also try redownloading the iso and reburning the image to disk.

---

### Post by arvevans on 2007-06-17
There are a number of checks you can make to insure that downloaded software is error free.  

Of course you already know that you have to burn bootable CDs as .iso image files (you got it to boot so you are OK thus far).

When you download Linux .iso disks, you also need to get the "MD5 Sum" and at Cd burn time compare that with the calculated "MD5 Sum" for the image that you are burning.  This pretty much insures that your have no download errors.

When you actually burn the .iso image CD, you need to set the option for "verify" so that the new CD will be compared with the .iso image file.

If you have done all this, you are pretty much assured that the install code is correct.

If you are still having errors in install, either the CD-ROM reader is making errors, or the PC hardware (usually memory) is causing errors.  If you are able to boot and run the Ubuntu Live CD version of Linux, then your problem may  be PC hardware errors instead of CD-read errors.
_._

---

### Post by Afrikprophet on 2007-06-17
thanks guys, 
I didi burn it at a slow speed (4x) but I didn't run  "MD5 Sum".
 I will be burning another copy this evening and checking it with the "MD5 Sum" ya'll are awsome:popcorn:

---

### Post by Afrikprophet on 2007-06-18
ok did the mds5 check and even burned it using the suggested software now when I try loading it I get this error
 Disk error BB, ax = 4200, drive 82

at a bit of a loss as to what I am doing wrong.

---

### Post by GMachine_24 on 2007-06-18
hi............first, don't feel bad. we've all had this problem at one time or another. here are my attempted solutions in order:

1)make sure you have a good quality cd/dvd to start. even if it's good quality, if it doesn't work, try another make/model/writing speed
2)burn your cd/dvd at 4x max, no matter what your burner and the discs say
3) make sure the CD/DVD is clean before attempting an install. use windex if you have to (or something similar)
4) try a different burning program (i like graveman and k3b) and not just the window that pops up when you install your blank disc
5)if you have 2 cd/dvd burners/players in your computer, try the other one :)
6. make sure your hard drive is good

usually just reburning the disc will solve the problem. however i have had to use the other steps at one or more times.

good luck.

gm

---

### Post by Afrikprophet on 2007-06-18
Thanks GM machine. I think it was the cdrs that I was using. They were pretty old, luckily I found a spindle that I got a few months ago, burned the image and it loaded with out a problem. Even the wireless connection was pretty easy to work out.
You all just saved my machine. Thanks!:o

---

