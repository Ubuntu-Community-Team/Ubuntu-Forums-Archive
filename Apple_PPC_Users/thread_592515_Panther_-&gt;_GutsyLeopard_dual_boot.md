---
title: "Panther -&gt; Gutsy/Leopard dual boot"
date: 2007-10-26
forum: Apple PPC Users
---

### Post by nursegirl on 2007-10-26
Hey!
I've been running solely Ubuntu on my work machine (an old Wintel box) since the Dapper beta, but I've decided that it's time to start using it at home as well.

I'm running a 1.42GHz G4 mini, and my plan has been to:

1) Buy a 250GB external hard drive & Leopard, while downloading Feisty
2) Partition the hard drive with Mac's Disk Utility & backup my Panther install with SuperDuper
3) Install Leopard on my internal hard drive (80 GB), keeping all my programs and files on it
4) Install Feisty on my internal hard drive, pointing my home folder to the external hard drive
5) Upgrade to Gutsy

Any suggestions, warnings, concerns, caveats? 

Thanks in advance!

---

### Post by sulobanks on 2007-10-27
Seems like a good plan to me, assuming you bought a good quality external drive and you don't plan to move it around much or turn it off.  The only warning I would ever give someone is that if you're going to use the external for your /home partition, you need to make sure and treat it as an internal drive in every respect. Accidentally leaving it at work could be really annoying. ;P  I myself am not the most responsible in that respect.  I could see myself saying "Oh, I'm just gonna backup this one thing on this other machine" and then forget and leave it somewhere on a day when I really need to get to my stuff.

Only other thing I would be cautious about is Gutsy.  I haven't exactly heard glowing reports about the ppc port yet.  Personally, I'm waiting another month to see if the live cd works.  I have yet to get it to boot on my ibook g4.  If the live cd won't boot, I'm sure not gonna upgrade in the hope that having it installed on my drive will somehow be better.

---

### Post by stmiller on 2007-10-27
Yeah should work fine as long as you point the Leopard and Gutsy installers each to their own specific places, during their upgrades. They will each ignore the other operating system partitions. Backup critical data to be safe, as always.

---

### Post by louden on 2007-11-13
Did this work for you? 

If so - how did you format your Gutsy partition?  I'm trying to do the same thing on a new 160 GB drive in an old PowerBook.

Thanks!
Dan

---

### Post by BladeMelbourne on 2007-11-14
I am running Gutsy on my 1.42 GHz PPC Mac Mini. It's in a dual boot configuration, however I don't really use 10.4. I sometimes start it up using Mac on Linux to play Flash content that doesn't work with gnash.

My only tips are:
1) Make sure your external drive is not formatted as NTFS
2) If you get a black screen when xwindows starts (after upgrading to Gutsy), you may need to install an older ATI Radeon display driver (I use xserver-xorg-video-ati_6.6.3-2_powerpc.deb)

---

