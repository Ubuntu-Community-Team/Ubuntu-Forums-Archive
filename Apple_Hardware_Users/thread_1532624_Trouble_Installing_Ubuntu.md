---
title: "Trouble Installing Ubuntu"
date: 2010-07-16
forum: Apple Hardware Users
---

### Post by kate mcgrath on 2010-07-16
Hey, 

I am new to Ubuntu and am having trouble getting it installed on my computer (I have a mac os x). I have successfully burned Ubuntu 10.04 onto a cd and can get my computer to boot it. 
The problem arises when I try to use ubuntu without changing my computer. The screen goes black and I have to shut my computer down to get any response at all. The same thing occurs no matter what option I choose when Ubuntu initially loads. 
I have tried the older version 9.10 with the same results. 
My frustration level is very high right now and I'm stumped! so any help would be appreciated. 

Thanks!
Kate

---

### Post by Rubi1200 on 2010-07-16
Hi Kate and welcome :)

We need some additional information please about your computer specifications, especially about what type of graphics card you have installed.

Also, do you want to dual-boot Ubuntu with Mac or get rid of Mac and only use Ubuntu?

These are things we need to know in order to offer solutions and advice.

Good luck!

---

### Post by kate mcgrath on 2010-07-16
okay, 

My comp is the iMac with the intwl core i5. It has a processor speed of 2.66GHz and a 4GB memory with 2342.25MB free RAM. 
I believe my graphics card is ATI Radeon HD 4850. It has 512MB VRAM. 

I want to do a dual boot I believe. I want to have the choice of either using Ubuntu or OS X.  The whole point of me getting Ubuntu is that I will be needing to use Linux based programs for my job soon. 

Cheers, 
kate

---

### Post by Rubi1200 on 2010-07-16
Thanks for the information.

This link has some workarounds you can try for the LiveCD:

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

I cannot offer advice for dual-booting with Mac because I have no experience with that. But I am sure if you search the forum you will probably find something.

I would just add that if you have had problems with both 10.04 and 9.10 you may want to consider some other options as well.

---

### Post by kate mcgrath on 2010-07-16
hey, 

So I've checked out your link and found that the Ubuntu version I have (10.04) has the option of "nomodeset" under F6. I don't have any of the other options listed on the webpage. 
When I deactivate the nomodeset and then try to run Ubuntu without installing it will allow me to go one step further than it has before. I can now see the Ubuntu logo and the loading dots loading. However once the loading is apparently complete my screen goes black again as before. 
I checked my disc for errors and it said it was fine. 

Any other suggestions? 
Thanks again!

---

### Post by Rubi1200 on 2010-07-16
Progress is always good :)

So, I have another suggestion and it goes like this:

When the CD starts up hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Move the cursor backwards using the arrow key and remove quiet splash;

Add the following parameter:

xforcevesa

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz xforcevesa --**

Now hit Enter and hopefully you will be at the desktop admiring Lucid Lynx 10.04

---

### Post by linuxman94 on 2010-07-16
Should have been posted in the "Apple Users" section.

---

### Post by lisati on 2010-07-16
Moved to "Apple Users"

---

