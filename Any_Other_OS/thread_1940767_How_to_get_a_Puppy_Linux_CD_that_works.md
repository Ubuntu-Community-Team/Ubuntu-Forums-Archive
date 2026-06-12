---
title: "How to get a Puppy Linux CD that works?"
date: 2012-03-14
forum: Any Other OS
---

### Post by malt loaf on 2012-03-14
Total beginner, so please spell it out for me!!

I need to make a Puppy Linux CD. Downloaded the Slacko 5.3.1 ISO file using a Vista PC. Using same PC tried to burn to a CD using BurnCDCC app. Will not burn, just keeps asking for a blank CD, which as far as I know is what I am giving it. The checksum on the ISO file is OK.

Possible problems?

Downloaded ISO using Vista?
Trying to burn using Vista machine?
Formatted the CD using a Vista machine?
Gave the CD a title?
Maybe should not have formatted the CD at all?

Something else?

---

### Post by nothingspecial on 2012-03-14
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by roger_1960 on 2012-03-14
Hi

Yes, a blank CD should not be pre formatted. Is this post to do with Ubuntu?

---

### Post by whatthefunk on 2012-03-14
A blank CD should be blank, as in nothing has ever been put on it.  Get a new blank CD and burn the iso onto it.

---

### Post by malt loaf on 2012-03-14
Guess that answers my question.  Thanks guys.

---

### Post by KosakiHook on 2012-05-12
Download ImgBurn from here: [http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)

and use this to burn your iso. I use this program to burn all my iso's, from Ubuntu, Linux Mint, Puppy Linux.

Then, put your CD or DVD in your optical drive, and reboot. You have to make sure your optical drive will boot prior to your hard drive. This can be set in the BIOS.

---

### Post by kalwisti on 2012-05-15
One other point about Puppy Linux which might be worth mentioning (since you said that you're a total beginner):

Puppy can load itself totally into RAM so that the CD (DVD) drive is then free for other purposes. In other words, once Puppy has booted up on your PC, you can remove the Live CD from your drive.

Puppy includes some useful utilities -- such as GParted (a partition editor) -- and its Live CD can help rescue files from borked Windows computers. 

One caveat about Puppy is that when you're using it via the Live CD, you are running as the root (/) user, so be careful.

---

