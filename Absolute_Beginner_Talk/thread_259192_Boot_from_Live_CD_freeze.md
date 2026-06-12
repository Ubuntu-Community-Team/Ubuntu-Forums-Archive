---
title: "Boot from Live CD freeze"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Staticdrifter on 2006-09-17
[COLOR="Navy"]Hello Ubuntu forum dwellers,

Very new to Ubuntu and naive at that.  So new in fact that I haven't actually seen Ubuntu in action.  I'm looking for some help from the *gurus* that you are.

_**Here's my problem:**_  I boot to the optical drive and fire up the Live CD. I select the first option which is Start or Install.  It then initializes and goes through all the different items and the complete bar finishes.  It then goes to a black screen with a blinking prompt in the top left corner. The prompt stops blinking and freezes.  

Any help would be greatly appreciated or if this has been answered already please point me in the right direction.[/COLOR] :)

---

### Post by charles.g.moore on 2006-09-17
I had the same problem and it was hardware related, mainly the vid card...
You should be able to boot under safe graphics mode, you should definitely check to see that your vid card is supported...
Im going to guess ATI?

---

### Post by onewisp on 2006-09-17
I have the same exact problem. I have Athlon 64 3500+, 2GB memory, Win XP install on first partition of first HD. I am wondering if anyone has run into this problem and how he/she fixes it. I have tried it using 64-bit and regular uBuntu 6.06 cd but they both froze after finished unpacking and loading everything. ](*,)

---

### Post by onewisp on 2006-09-17
> **charles.g.moore said:**
> I had the same problem and it was hardware related, mainly the vid card...
You should be able to boot under safe graphics mode, you should definitely check to see that your vid card is supported...
Im going to guess ATI?

Do you know where I can check out the compatibility list?

---

### Post by charles.g.moore on 2006-09-17
> **onewisp said:**
> Do you know where I can check out the compatibility list?
I think its here...
[http://www.ubuntuforums.org/archive/index.php/t-2457.html](http://www.ubuntuforums.org/archive/index.php/t-2457.html)

Sorry I meant here:
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by welshboy on 2006-09-17
I had the same problem on my computer, but I found that it was something to do with my DVD-RW drive, i put in a normal CD-Rom drive and it worked fine.

welshboy

---

### Post by Staticdrifter on 2006-09-17
[COLOR="Navy"]> **charles.g.moore said:**
> I had the same problem and it was hardware related, mainly the vid card...
You should be able to boot under safe graphics mode, you should definitely check to see that your vid card is supported...
Im going to guess ATI?

I should have added my specs #-o ...here they are:

Asus M2N-SLI Deluxe
AMD Athlon 64 X2 4200+
Two nvidia 7900 GT GPUs in SLI
2g RAM
Plextor PX-750A dvr
Western Digital 400g HDD
Hanns.G JW199D 19" widescreen [/COLOR]

---

### Post by bankrupt on 2006-09-17
I think I'm having the same problem as you guys and I can't figure it out as this is my first experience with Linux.  When I select the first option on the live CD "boot or install Ubuntu" my computer gets to the screen where an "X" appears and then turns a dark red color.  A cream colored bar with the Ubuntu logo then shows up and that's as far as the boot goes, nothing else happens.    Now if I use the safe mode option the CD boots through the whole way and works.  I'm assuming it's probably an issue with the video card, but I don't know where to start or how to fix it.  If anyone could help me figure this out I'd appreciate it.  Here are my computer specs:

Athlon 64 3200+
EPoX 9NPA +Ultra nForce 4 mobo
eVGA 7800 GT video card
NEC ND-3540A DVD/CD-R
2 Gig of Corsair value RAM
2x 250 GB Seagate HDD

I'm using the 32 bit live CD.

---

### Post by liveforfunnow on 2006-10-22
i've got the same issue with the live CD, and an eVGA 7800 GT as well. i've tried all manners of ubuntu - 6.06 both i386 and AMD, and 6.10 for those as well. safe mode doesn't help, though. does any one know why? i posted this problem here:
[http://ubuntuforums.org/showthread.php?p=1642720#post1642720](http://ubuntuforums.org/showthread.php?p=1642720#post1642720)

but the proposed solutions were a no-go (i haven't tried the alternate CD yet)...

---

### Post by liveforfunnow on 2006-10-22
ok, fixed: i ran safe graphical mode from the 6.06 liveCD, and it installed no problem.

---

