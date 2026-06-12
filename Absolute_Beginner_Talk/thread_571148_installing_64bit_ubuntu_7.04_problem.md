---
title: "installing 64bit ubuntu 7.04 problem"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by blindfolds7 on 2007-10-09
ok, so I'm trying to install feisty fawn on my laptop (i have vista, i'm doing the dual boot thing) but this is what is happening: I put the disc in and restart the computer and then I get this screen saying 

Starting PC DOS....
Preparing to start your computer
yadayadayada
random info about the comptuer
Mouse driver installed successfully
A:\>_

And now I am lost.  If someone could help me out that would be awesome, I don't know if this is part of the installation or anything, but I can't find anything about this. Thanks for any help!

---

### Post by OneMoreOfThem on 2007-10-09
It sounds like your computer is booting from the floppy drive.  You need to make it boot from the CD drive.  You can do this by either changing the "boot from" option in BIOS, or, if your motherboard has a boot option you can use that and force it to boot from the CD just that time. (It is F11 as it is booting up on my motherboard, not sure what yours is, but it should say just after you power up the computer.)

---

### Post by blindfolds7 on 2007-10-09
I already have it set to boot from the cd drive. Any other suggestions?

---

### Post by OneMoreOfThem on 2007-10-09
Does the CD start to run before you get the PC DOS message?

---

### Post by RomeReactor on 2007-10-09
Hi. Did you download it [from here]("http://www.ubuntu.com/getubuntu/download")? and did you burn it as an image, not as a data CD?

---

### Post by blindfolds7 on 2007-10-09
like can I hear it running? I can hear it running if that's what your asking, but otherwise the screen is just black before that.

---

### Post by blindfolds7 on 2007-10-09
I did download it from there, and ISO is the same as image right? because it's ISO... If that helps

---

### Post by misfitpierce on 2007-10-09
Usually keep tapping F10-12 while booting and screen should come up to select force boot to device. Choose CD. Most computers use between those keys. :)

---

### Post by OneMoreOfThem on 2007-10-09
ISO is right.  Does the light on the CD drive come on before the message?  

Did you MD5 the file before burning it to disk?

---

### Post by blindfolds7 on 2007-10-09
did I mention I'm a noob?

---

### Post by blindfolds7 on 2007-10-09
Md5?

---

### Post by OneMoreOfThem on 2007-10-09
> **blindfolds7 said:**
> did I mention I'm a noob?

That's alright, me too.  

I'll see if I can find the link and info for the MD5.  It is a type of checksum program to make sure the image was downloaded without errors.

---

### Post by blindfolds7 on 2007-10-09
also the cd drive does light up, and if I keep tapping f10, for like a second the screen says something about the cd drive and then that screen goes away and it goes back to the one with the a:\>

---

### Post by blackcp on 2007-10-09
> **blindfolds7 said:**
> Md5?

[http://us.releases.ubuntu.com/7.04/MD5SUMS](http://us.releases.ubuntu.com/7.04/MD5SUMS)

---

### Post by RomeReactor on 2007-10-09
> **blindfolds7 said:**
> Md5?

It's a way to verify the integrity of your file; that your .ISO file is indeed correctly downloaded. I'm beginning to think this is a BIOS issue, though. Have you tried booting your PC from the CD before?

---

### Post by OneMoreOfThem on 2007-10-09
This is where I got my download:
[http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=amd64&mirror=http%3A%2F%2Fftp.wwc.edu%2Fpub%2Fmirrors%2Fubuntu-releases%2F&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=](http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=amd64&mirror=http%3A%2F%2Fftp.wwc.edu%2Fpub%2Fmirrors%2Fubuntu-releases%2F&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=)

Here is the MD5 program download:
[http://www.nullriver.com/index/products/winmd5sum](http://www.nullriver.com/index/products/winmd5sum)

This page will tell you how to use it:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

BTW  does you CD drive work for other disks?  Can't hurt to make sure.

---

### Post by blindfolds7 on 2007-10-09
I know my disc drive works, and I have booted my computer from the cd before.  I'll try this md5 thing though.

---

### Post by arpanaut on 2007-10-09
> **blindfolds7 said:**
> 
Starting PC DOS....
Preparing to start your computer
yadayadayada
random info about the comptuer
Mouse driver installed successfully
[COLOR="Red"]A:\>[/COLOR]_

If you are getting that prompt then I believe that you burned as a Boot Disk or Bootable disk in Windows not burnt as an image.

There is a bunch of good information in the stickies at the top of the page.

GL!

Here you go...     
Once you've obtained the CD image, burn it to CD with this guide
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by blindfolds7 on 2007-10-09
ok I ran that MD5 thing and they didn't match... which doesn't seem good.

---

### Post by dptxp on 2007-10-09
> **blindfolds7 said:**
> ok I ran that MD5 thing and they didn't match... which doesn't seem good.

you should use torrents to download iso files.

---

### Post by blindfolds7 on 2007-10-09
Ok, I'm going to try downloading this again and burning it properly. Hopefully that will fix my problem. Thanks so much for all the help!

---

### Post by RomeReactor on 2007-10-09
If you still have the .ISO file in windows, you don't need  to download it again; just use [InfraRecorder]("http://infrarecorder.sourceforge.net/") to burn the .ISO as an image, as instructed by [the link posted by arpanaut]("https://help.ubuntu.com/community/BurningIsoHowto").

---

