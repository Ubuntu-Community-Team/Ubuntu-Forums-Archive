---
title: "installation"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Ayunami on 2007-12-04
when i put in the disk for a blank HDD i have i click start or install ubuntu,
then it all goes through but comes up with theese errors:
148.777207] Buffer I/O error on device fd0, logical block 0
153.625889] ata6.01: failed to set xfermode (err_mask=0x40)
xxx.xxxxxx] Buffer I/O error on device fd0, logical block 0
xxx.xxxxxx] Buffer I/O error on device fd0, logical block 0
xxx.xxxxxx] ata6.01: failed to set xfermode (err_mask=0x40)
xxx.xxxxxx] Buffer I/O error on device fd0, logical block 0
xxx.xxxxxx] Buffer I/O error on device fd0, logical block 0
xxx.xxxxxx] Buffer I/O error on device fd0, logical block 0


the "xx.xxxxx" are different numbers, but after this it all loads up, and comes to the ubuntu screen where i hear some music, then it all freezes...


please help

thank you in advance.

~

---

### Post by banewman on 2007-12-04
The errors are probably due to your hardware - can you tell us the computer specs?
Is it a laptop?

---

### Post by Ayunami on 2007-12-04
its pc
umm the hdd im trying to get it on is 160gig
1gig ram
cpu 2.67 ghz core 2 duo
foxcon 975X7AB motherboard
son dvd/rw 
400w psu
nvidea 8600 graphics card

---

### Post by Ayunami on 2007-12-04
anyone got any ideas?

---

### Post by Ayunami on 2007-12-04
~

---

### Post by fineas on 2007-12-04
First, something you ought to have read before posting ([http://ubuntuforums.org/showthread.php?t=65842](http://ubuntuforums.org/showthread.php?t=65842))
*As a side note, cross-posting (posting the same question in more than one place) is likewise considered bad form. However, because these forums move fast, bumping a thread (posting an empty reply just to move the thread to the top of the stack) is acceptable.*

Now, about your installation problems:
Have you checked your installation CD for defects? Check here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto).

---

### Post by Ayunami on 2007-12-04
yeh, i got the CD from ubuntu it was sent to me. and i tried 2 of them that they gave me, both with same errors

---

### Post by coolbrook on 2007-12-04
Are you using the latest BIOS?  It may be the chipset that your CD/DVD drive is using. Do you only have the one CD readable drive?  If not then try the other one. There are a number of solutions on here. YMMV.  I tried all of them to no avail.

In my case, I just happened to have Ubuntu 6.10 (Edgy Eft CD) which worked for me when Feisty and Gutsy CD's were giving me problems.   I used the Edgy CD to install then I installed all updates, upgraded to Feisty (7.04), installed all Feisty updates and then upgraded to Gutsy (7.10.)

Seeing as you ordered the CD then I suppose this isn't the practical solution.  Ask a friend if you can hook up to their broadband network and give it a try.

---

### Post by khgiese on 2007-12-04
I hope I am not way off base here.
It looks like a hardware error.
Is this a new system?
 Have you tested the memory? 
It also might be the controller chip.

---

### Post by philinux on 2007-12-04
Those errors are hardrive errors.

Edit - except fd0 is the floppy drive

---

### Post by billgoldberg on 2007-12-04
I got similar errors when installing ubuntu 7.10 on my pc.

solution;
remove dust from disk.

---

### Post by Ayunami on 2007-12-04
Well i ran it once, and it worked ages ago. this is a different HDD however.

also there is no floppy drive installed in my pc

the memory is also fine. i had it checked out

---

### Post by philinux on 2007-12-04
> **Ayunami said:**
> when i put in the disk for a blank HDD i have i click start or install ubuntu,
~

Can you explain what you mean by [COLOR="Red"]put in a disk for a blank hdd[/COLOR]

You mean a live cd,  which version?

---

### Post by Ayunami on 2007-12-04
i mean i have a second HDD that i wiped, an i use the disk i got from delivery through ubuntu

my other HDD is the one i use for windows

---

### Post by Ayunami on 2007-12-04
bump

---

### Post by coolbrook on 2007-12-04
Try installing with your CD/DVD drive on IDE2 while leaving your target hard drive on IDE 1.  That's worked for some.

---

### Post by Ayunami on 2007-12-04
hm tried that, didnt work, any other ideas?

---

### Post by Ayunami on 2007-12-04
bump

---

### Post by khgiese on 2007-12-04
What are your BIOS settings for the floppy drive? is it set to none?
Just a thought, but if your BIOS are set to say a floppy drive is present and there is none, Ubuntu might be trying to access a phantom drive.

---

### Post by khgiese on 2007-12-04
I did a quick search of the forums on your error and found this link.
[http://ubuntuforums.org/showthread.php?t=537865](http://ubuntuforums.org/showthread.php?t=537865)
Hope it helps.

---

### Post by Ayunami on 2007-12-04
i looked through it and it says its only a solution for old laptops that dont have requirements, but i do have the requirements

---

### Post by Ayunami on 2007-12-04
bump

---

