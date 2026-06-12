---
title: "Old Dell Computer"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by cairnsww on 2007-12-17
I have an old Dell desktop - it was new in 1999 - and I have been running Ubuntu 6.06 on it quite happily. But I upgraded to 7.10 on my other (much newer) machine recently and decided that it was time that the Dell followed suit.

I have an Ubuntu 7.10 install disk from ShipIt. Unfortunately, it will not load on the Dell. I choose the Run / Install option and it seems to start OK but then just freezes. Blank screen, no disk activity.

I thought it might be a bad disk and tried it as a live CD on my HP notebook (from work, doomed to run Windows, shame). It worked fine. (Although, when I told it to do an integrity check on the disk, it too hung).

Any idea? Nothing wrong with 6.06 of course, but it would be nice to have the whole family at the same level.

---

### Post by jken146 on 2007-12-17
Well, if the intrgrity check didn't succeed then maybe it's a bad burn.  [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

Could you post the specs of that Dell please?

---

### Post by CJ56 on 2007-12-17
Have you tried downloading the alternate install CD? I had exactly the same problem trying to put Ubuntu 7.10 on my old Dell laptop. Then I burned an alternate install  CD (which uses clunky old text instructions instead of GUI-based things to run the installation procedure) and that went in just fine. The text instructions are very clear and easy to follow - better in some ways than the GUI version.

---

### Post by cairnsww on 2007-12-17
It calls itself a Dell Optiplex GX110 for what that is worth. 

It has 18.65 GBytes of hard disk.

I confess that I don't know how to find what processor it has (although the sticker says "Intel Inside"). Device manager tells me that the processor type is "Unknown".

---

### Post by cairnsww on 2007-12-17
> **CJ56 said:**
> Have you tried downloading the alternate install CD? I had exactly the same problem trying to put Ubuntu 7.10 on my old Dell laptop. Then I burned an alternate install  CD (which uses clunky old text instructions instead of GUI-based things to run the installation procedure) and that went in just fine. The text instructions are very clear and easy to follow - better in some ways than the GUI version.

No - I am just using the ShipIt disk. I would rather not download the install disk at the moment because of bandwidth - might be able to get a faster access later this week.

---

### Post by jken146 on 2007-12-17
I too have had much success with alternate CDs where live ones have failed.

---

### Post by tgalati4 on 2007-12-17
I presume that you have 256 MB of RAM and at least a 256 MB swap disk.  Otherwise the live disk will hang.  You may get away with 128 MB of RAM, but Gutsy will run slow.

I installed Linux Mint 4 XFCE which runs pretty well on a old Dell GX1 (PIII, 500 MHz, 768 MB RAM (maxed out))

---

### Post by Martin Witte on 2007-12-17
a little surfing makes me assume the cpu in this dell is a 500MHz Pentium III, those machines came typically with 128 Mb, which explains the hanging live disk. if you really have 128Mb I wouldn't go for a gnome desktop, i'd rather move to Xubuntu (XFCE desktop based Ubuntu)

---

### Post by jken146 on 2007-12-17
> **Martin Witte said:**
> a little surfing makes me assume the cpu in this dell is a 500MHz Pentium III, those machines came typically with 128 Mb, which explains the hanging live disk. if you really have 128Mb I wouldn't go for a gnome desktop, i'd rather move to Xubuntu (XFCE desktop based Ubuntu)

+1 to that, also I should point out that the Xubuntu live CD will hang on less than 192Mb of RAM, so use the alternate CD.

---

### Post by T-O-M on 2007-12-17
I had the same problem with a Dell GX240.  The graphical install would hang so I attempted the non-graphical install with the alternate CD.  It seemed to be going just fine until partitioning (where I am now).  It has been at 33% for about an hour now.  I dont think I want to bail on it quite yet, the keyboard is responsive.

---

### Post by mramsey on 2007-12-17
I have installed on several Optiplex GX110's using the alternate CD. You are probably only running about 256MB RAM which is most likely the issue when using the Live CD. I tend to find that the installs go a little better with the Alternate version.  good Luck.:)

---

### Post by T-O-M on 2007-12-17
> **mramsey said:**
> I have installed on several Optiplex GX110's using the alternate CD. You are probably only running about 256MB RAM which is most likely the issue when using the Live CD. I tend to find that the installs go a little better with the Alternate version.  good Luck.:)


Did you use the text based installer?  Also, any idea why it appears to be hanging at 33% when partitions are formatting?

---

### Post by tgalati4 on 2007-12-17
Could be a bad spot on the disk so it's trying to reread the sector marks that it laid down.  Give it an hour and if it doesn't recover, reboot.  If it's an old disk, you may have better luck prepping it with a low-level format using Ultimate Boot CD.  

Once you get it partitioned, from the live CD:

>fsck -cc /dev/sda1

That will check for bad blocks.  Takes a long time.

---

### Post by sl_guy on 2007-12-17
I have even an older desktop (Pent II 300Mhz, 128MB) running 7.10. I downloaded the alternate ISO and burned it @ 8x, did a CD check and it failed. I burned it again @ 4x and everything ran smoothly. Ubuntu runs kinda slows with my current desktop, but oh well....it's about 10 years old...wat do u expect

---

### Post by Papa-san on 2007-12-17
I'd just stick with 6.06. if it ain't broke, don't fix it!

---

### Post by cairnsww on 2007-12-17
Thanks guys - I am not sure what memory I have. How do I find out?

But remember - this machine runs 6.06 fine. No problems (OK, a bit slow to start). It is the 7.10  Live CD that won't load.

---

### Post by cairnsww on 2007-12-17
> **Papa-san said:**
> I'd just stick with 6.06. if it ain't broke, don't fix it!

Probably the smartest comment of all!

---

