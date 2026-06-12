---
title: "I broke my parents Windows machine! Help?"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by curiousnoob on 2008-03-25
Preaching the wonders of Ubuntu to my parents while visiting them I convinced them to set up a dual boot so they could use Ubuntu or Linux.
All things went well until two weeks after I left.  They can no longer get into either and get the following message when booting up:

"A problem has been detected and Windows has been shut down to prevent damage to your computer"
"UNMOUNTABLE_BOOT_VOLUME"
Technical in
***STOP:0X000000ED"0X827D0868'0XC000185'0X00000000'0X0000000'"

I have read about people getting this when a partition is screwed up but this setup worked for weeks with the machine frequently shut down and turned back on.
For the mean time they are using an Ubuntu Live disc so they can at least get online but I really need to fix this.  
The problem is exacerbated by the fact that they live on the other side of the country and I can't get my hands on the actual PC.
Any ideas/help?

---

### Post by 1875 on 2008-03-25
May well be a corrupted hard drive. Can they access any data on the drive using the Live CD ?

---

### Post by Dr Small on 2008-03-25
That's definately a Windows Error... they are generally senseless.
And what is wrong that they can not boot into Ubuntu?

Dr Small

---

### Post by t0p on 2008-03-25
To fix your parents' broken box, I'd suggest that they reformat the hard disk and install Ubuntu as the sole OS.  Hell, *anything* is better than that microshaft stuff.

(You may think I'm being a hypocrite, seeing as I dual-boot gutsy and xp.  But I can assure you, if the Windows fell off my box I wouldn't lose a moment's sleep.)

---

### Post by curiousnoob on 2008-03-25
> **Dr Small said:**
> That's definately a Windows Error... they are generally senseless.
And what is wrong that they can not boot into Ubuntu?

Dr Small

GRUB never comes up.

---

### Post by Helios38 on 2008-03-25
perhaps the MBR got messed up.


thats windows for ya.


only solution i can think of is a wipe of the hard drive

---

### Post by heartburnkid on 2008-03-25
If it took two weeks for Vista to start blue-screening, I doubt it had anything to do with your repartition.  Likely Windows crapped itself some other way.

Vista probably overwrote part of the MBR somehow.  Microsoft OS's don't really like to play well with others...

---

### Post by fela on 2008-03-25
so why do you dual boot? i only have ubuntu on my PC, never ever used windows natively in my own house. :P

---

### Post by Dr Small on 2008-03-25
> **Helios38 said:**
> perhaps the MBR got messed up.


thats windows for ya.


only solution i can think of is a wipe of the hard drive
How about installing GRUB back over the MBR with the SuperGrub Disc?

---

