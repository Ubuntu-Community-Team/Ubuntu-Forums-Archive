---
title: "Installation does not start"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by r3a7amd on 2007-07-06
Hi there,

I'm a newbie here and I really like to install Ubuntu but faced this problem and don't know how to solve it. I downloaded the ISO file and did that MD5 thing and checked the hash number and all that worked fine. Then I burned it to a CD and boot my computer and when I choose "Install the Ubuntu" the application just freezes and nothing happens.

What should I do?

---

### Post by twiceasworn on 2007-07-06
What are the specs of your system?  What portion of the install does it freeze on?  Are you able to boot up the live cd and play around with it?

---

### Post by p_quarles on 2007-07-06
What are your system specs? You might need to use the alternate install CD.

---

### Post by r3a7amd on 2007-07-06
Well, I have windows XP SP2

When I insert the CD and boot the first page of Ubuntu appears which has options like Install / check memory / and etc. but when I click the Install and then nothing happens, I leave it for half an hour but the installation doesn't even start.

I mounted the ISO file on a CD using MagicISO because I had a problem with the InfraRecorder.

Please help I want to run this OS so badly.

---

### Post by p_quarles on 2007-07-06
"System specs" means your memory, hard drive space, video card, processor speed, etc. What are those?

---

### Post by r3a7amd on 2007-07-06
Memory: 640 MB
Hard Drive: Partition 1- C: 54 Gig - Contains Windows XP
                    Partition 2- F: 20 Gig - Free Partition
Video Card: Nvidia GeForce FX 5500
Processor: Intel(R) Pentium(R) 4 CPU 2.66 GHz
OS: Microsoft Windows XP (Home Edition) SP2

---

### Post by Raineer on 2007-07-06
Your specs are fine for the Live CD, I'm not really sure why it's freezing.  I don't know that I'd try it via MagicISO though, I know that program and love it, but I'm not sure that the Live CD will install that way.

Maybe just look for another way to burn the ISO, it sounds like you could have a bad copy.

---

### Post by Crafty Kisses on 2007-07-06
> **r3a7amd said:**
> Hi there,

I'm a newbie here and I really like to install Ubuntu but faced this problem and don't know how to solve it. I downloaded the ISO file and did that MD5 thing and checked the hash number and all that worked fine. Then I burned it to a CD and boot my computer and when I choose "Install the Ubuntu" the application just freezes and nothing happens.

What should I do?

You can try using the alternate CD Installer.

---

### Post by r3a7amd on 2007-07-06
then What should I do, after Downloading the ISO I checked the image with winMd5Sum to be sure I have the full image and it was fine.

Do you recommend any other image burning software that I can use to burn that image?

---

### Post by r3a7amd on 2007-07-06
> **Codename said:**
> You can try using the alternate CD Installer.


I'm sorry but can you be more simple, I mean what is alternate CD Installer? and one more thing can I use a DVD-RW instead of a CD?

---

### Post by r3a7amd on 2007-07-06
any suggestion?

---

### Post by bodhi.zazen on 2007-07-06
Check out these links :

Burning :

[https://help.ubuntu.com/community/CdDvdBurning](https://help.ubuntu.com/community/CdDvdBurning)

[http://www.petri.co.il/how_to_write_iso_files_to_cd.htm](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm)



And install from alternate CD :

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by twiceasworn on 2007-07-06
The alternate cd is just a test based install instead of the graphical gui based installer.  It sounds like your disc is messed up to me.  I would suggest either using the alternate install (using the link above) or re-burning the disc.  Sometimes things just dont burn quite right.  I had it happen when i burned feisty to a cd, the first one didnt work and would hang, just like yours.  So i re-burned it and all was happy.

---

### Post by p_quarles on 2007-07-06
You can get the alternate CD the same way as the live CD: go to the Ubuntu download site, select your system type, etc. The only difference is that you check the box that says "alternate" before you download it.

The alternate CD doesn't have the live desktop, but it has a more robust installer. I've found that it works on many systems that for whatever reason can't boot the live CD.

As for image burning software for Windows: ImgBurn works flawlessly, and it's free/open source. If you have any doubts about the software you used, try that.

Also, the installation CDs (live & alternate) both have a function to check the integrity of the disk after you boot it up. You might run that and see if it burned all right.

---

### Post by r3a7amd on 2007-07-06
Hi again,

I did what you guys told me, I downloaded the alternate image and burned it to a CD and it worked fine till I received this message when I wanted to install the OS:
"Your CPU does not support long mode. Use a 32bit distribution" 

now what should I do or what did I do wrong?

why cant everything go smoothly!!?

---

### Post by p_quarles on 2007-07-06
Did you download the 64-bit version of Ubuntu? Based on the error message you got, I'm guessing you did. Go and get the 32-bit version (the default).

---

### Post by r3a7amd on 2007-07-06
Yes your right I did download the 64bit, but you know what threw me off is this: 64bit AMD and Intel computers : since my computer is Intel I thought this might be the one. Anyways thnx 4 ur help.

---

### Post by p_quarles on 2007-07-06
There are a few, newer Intel processors that are 64-bit (I believe it's just the Pentium D and the Core 2). However, the 32-bit version of Ubuntu is a lot friendlier on most systems, including the 64-bit ones. 

Hope it works this time.

---

