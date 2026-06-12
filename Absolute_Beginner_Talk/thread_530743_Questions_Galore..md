---
title: "Questions Galore."
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by 4Real on 2007-08-20
Hey , I'm not having any problems with Ubuntu , just some questions.

1. Can **WINE** run every single Windows Application???

2. I have 2 ** hard drive**s and thinking of plugging them both in and trying to reformat them to become one. Does Ubuntu have a option for that or is that even possible?

3. Do you think Ubuntu would run good on a 9gb , 667 mhz , Pentium III Computer?

4.  Similar to question 1 has anyone ran these programs on WINE?

Windows Movie Maker , WinZip , WMP , Photoshop , PC Games...??? The thing is I don't want to dual boot to my XP and have to run the programs extremely slow. I want Ubuntu as my OS.

:guitar:

---

### Post by buzzmandt on 2007-08-20
> **4Real said:**
> Hey , I'm not having any problems with Ubuntu , just some questions.

1. Can **WINE** run every single Windows Application???

2. I have 2 ** hard drive**s and thinking of plugging them both in and trying to reformat them to become one. Does Ubuntu have a option for that or is that even possible?

3. Do you think Ubuntu would run good on a 9gb , 667 mhz , Pentium III Computer?

4.  Similar to question 1 has anyone ran these programs on WINE?

Windows Movie Maker , WinZip , WMP , Photoshop , PC Games...??? The thing is I don't want to dual boot to my XP and have to run the programs extremely slow. I want Ubuntu as my OS.

:guitar:

1. No, Not to many actually, but getting better

2. 2 hard drives? or 2 partitions?  2 partitions can become one, 2 hard drives cannot

3.  yes, you might also look at xubuntu, great for older systems.

4. movie maker: haven't used
 winzip-ubuntu has  a good zip/unzip, do you need specifically winzip?
wmp, windows media player?  ubuntu has good players, mplayer, vlc, xine, and more
pcgames, under wine, it's kinda hit and miss, you can look at [http://appdb.winehq.org/](http://appdb.winehq.org/) to check..

you will probably find that linux has many apps that can replace your windows apps....except for games  :(.  There are many games that will run in wine, cedega, and/or natively, depends on the game

---

### Post by gn2 on 2007-08-20
Here's my answers

1= No

2= Don't know never tried but probably yes.

3= Reasonably OK but Xubuntu better: [http://www.xubuntu.org/get](http://www.xubuntu.org/get) [https://help.ubuntu.com/community/InstallingXubuntu](https://help.ubuntu.com/community/InstallingXubuntu)

4= Never used Wine prefer native apps and don't play games on PC.

---

### Post by bodhi.zazen on 2007-08-20
> **4Real said:**
> Hey , I'm not having any problems with Ubuntu , just some questions.

Bring 'em on ...

> 1. Can **WINE** run every single Windows Application???

No

See here : [http://appdb.winehq.org/](http://appdb.winehq.org/)

(the site looks like it is down atm ...)

> 2. I have 2 ** hard drive**s and thinking of plugging them both in and trying to reformat them to become one. Does Ubuntu have a option for that or is that even possible?

Yes, look at LVM ...

> 3. Do you think Ubuntu would run good on a 9gb , 667 mhz , Pentium III Computer?

Define "good"

> 4.  Similar to question 1 has anyone ran these programs on WINE?

Windows Movie Maker , WinZip , WMP , Photoshop , PC Games...??? The thing is I don't want to dual boot to my XP and have to run the programs extremely slow. I want Ubuntu as my OS.

:guitar:

See first link ...

---

### Post by bodhi.zazen on 2007-08-20
> **buzzmandt said:**
> 2 hard drives? or 2 partitions?  2 partitions can become one, 2 hard drives cannot

Take a look at LVM ...

---

### Post by buzzmandt on 2007-08-20
> **bodhi.zazen said:**
> Take a look at LVM ...
i stand corrected, thanks bodhi, i've learned another thing today  :)

---

### Post by 4Real on 2007-08-20
Ok thanks I will try it out and let you know. I think combining 2 hard drives as one is called raid array.

---

### Post by bodhi.zazen on 2007-08-20
Oh, you are asking about RAID, that is different :

[http://www.howtoforge.com/ubuntu_dapper_raid_system](http://www.howtoforge.com/ubuntu_dapper_raid_system)

---

### Post by 4Real on 2007-08-20
Is there a tutorial for Fiesty Faun?

---

### Post by Hobo Joe on 2007-08-20
> **4Real said:**
> Hey , I'm not having any problems with Ubuntu , just some questions.

1. Can **WINE** run every single Windows Application???

2. I have 2 ** hard drive**s and thinking of plugging them both in and trying to reformat them to become one. Does Ubuntu have a option for that or is that even possible?

3. Do you think Ubuntu would run good on a 9gb , 667 mhz , Pentium III Computer?

4.  Similar to question 1 has anyone ran these programs on WINE?

Windows Movie Maker , WinZip , WMP , Photoshop , PC Games...??? The thing is I don't want to dual boot to my XP and have to run the programs extremely slow. I want Ubuntu as my OS.

:guitar:

1. No

2. You can't combine them as one, as far as I know, but you can still use both of them, such as one for data, the other for the programs and such.

3. I may not say 'good', but yes, it should run without any issues at a decent speed.

4. There are fabulous and far superior alternatives to WMM, Winzip, and WMP, as for photoshop, there is alternatives for that, or you could also run it in wine.
Also, dual booting will have nothing to do with the speed of your system. At all.

What's up with all the Windows apps anyway? I hate those with a burning passion! :mad:

---

### Post by bodhi.zazen on 2007-08-20
> **Hobo Joe said:**
> 
2. You can't combine them as one, as far as I know, but you can still use both of them, such as one for data, the other for the programs and such.

LOL Hobo Joe ...

Look up ^^

Check out LVM or in this case I think the OP is asking about RAID

---

### Post by SoloSalsa on 2007-08-20
I have no idea what LVM is.  If bodhi had not mentioned it, then I would have said 'no'.  But, LVM is software.  Though soft RAID works, it is not as good as true, hard, RAID controllers, so I assume the same for LVM.  Anyway, RAID 0 can stripe the disks, and even potentially boost performance compared to using single disks.  But if something bad happens, then virtually all is lost.  If you do not want RAID, you could try JBOD (which a lot of RAID controllers can do, too).  An array of 'just a bunch of disks' puts disks right after the other, and pretends they are one.  So a file toward the end of one disk carries right over, onto the other disk.  It should have no affect on performance, and everything but files on the gap are recoverable.

---

### Post by gatman3 on 2007-08-21
Wine runs almost no Windows programs, in my experience.  Maybe old Windows 98 compatible stuff.

If you need to run Windows programs (first ask yourself why you are using Linux...) try VMware.  You'll need to install a real copy of Windows on it, but it runs pretty much anything.

---

