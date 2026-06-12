---
title: "Dual Boot didn't install?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by co.link on 2007-10-27
I made a primary NTFS Partition for my windows xp and installed that first, then I made an extended partition with several logical drives inside for Ubuntu 7.10 ( the swap, / and /home).  After the install, the.. GRUB(?) loader didn't show up, and windows automatically loaded.

What did I miss?  Why doesn't it dual boot?  Should I have installed Ubuntu on the primary drive?  How do I get it to dual boot now, without reinstalling any operating systems?



Where do I send a... guess you would call this a complaint?  Hickups like these can very quickly offput new users, like myself.  This is one of those features that really should just work.  I also had a couple other issues that were bothersome.  I'm worried that a plethora of minor issues like this one can derail adoption.  I tried installing 7.04 and only had trouble.  I had previously advertised to my friends wanting to try to install it, so when they asked what happened, I had to tell them that the program was just not ready.  Already I'm seeing this new version going down the same route.

---

### Post by overdrank on 2007-10-27
> **co.link said:**
> I made a primary NTFS Partition for my windows xp and installed that first, then I made an extended partition with several logical drives inside for Ubuntu 7.10 ( the swap, / and /home).  After the install, the.. GRUB(?) loader didn't show up, and windows automatically loaded.

What did I miss?  Why doesn't it dual boot?  Should I have installed Ubuntu on the primary drive?  How do I get it to dual boot now, without reinstalling any operating systems?



Where do I send a... guess you would call this a complaint?  Hickups like these can very quickly offput new users, like myself.  This is one of those features that really should just work.  I also had a couple other issues that were bothersome.  I'm worried that a plethora of minor issues like this one can derail adoption.  I tried installing 7.04 and only had trouble.  I had previously advertised to my friends wanting to try to install it, so when they asked what happened, I had to tell them that the program was just not ready.  Already I'm seeing this new version going down the same route.

Hi and you may try to reinstall the grub and this thread has great info
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Hope this helps and good luck! :KS

---

### Post by stomponthis on 2007-10-27
Sounds like the ubuntu partition isnt active.
Try booting with the liveCD, opening the partition tool in the 'system' menu and checking the properties of the partitions and set active to the linux partition.
Check your grub file if it does not give you a choice to boot XP from a menu after you make the linux partition active.
```
sudo gedit /boot/grub/menu.lst
```

Should have a line in it like below to boot XP

```

title		Windows 95/98/NT/2000
root		(hd0,0)
makeactive
chainloader	+1

```

Don't give up yet, I used to only use windows, now I don't know why I ever did?!

---

### Post by co.link on 2007-10-28
I tried setting the "/" as boot, and then I tried setting "/home" to flag boot.  Both didn't work.  What am I missing?  Should I reinstall Ubuntu with the "/" set as boot?  What do I need to do to get this to start working?

---

### Post by oilchangeguy on 2007-10-28
> **co.link said:**
> I made a primary NTFS Partition for my windows xp and installed that first, then I made an extended partition with several logical drives inside for Ubuntu 7.10 ( the swap, / and /home).  After the install, the.. GRUB(?) loader didn't show up, and windows automatically loaded.

What did I miss?  Why doesn't it dual boot?  Should I have installed Ubuntu on the primary drive?  How do I get it to dual boot now, without reinstalling any operating systems?



Where do I send a... guess you would call this a complaint?  Hickups like these can very quickly offput new users, like myself.  This is one of those features that really should just work.  I also had a couple other issues that were bothersome.  I'm worried that a plethora of minor issues like this one can derail adoption.  I tried installing 7.04 and only had trouble.  I had previously advertised to my friends wanting to try to install it, so when they asked what happened, I had to tell them that the program was just not ready.  Already I'm seeing this new version going down the same route.


send a complaint? for what? when the problem is not the operating system, but the operator. what has made you belive that you have to go thru all of the trouble you did, to make partitions? because you don't need to. the best way is to use gparted from the live cd. and make your windows partition smaller. then allow ubuntu to use the space you set for it, or use the largest free space. but allow it to create it's own partitions in whatever space it uses.

also, are you sure you actually installed ubuntu? just running the live cd does not install it. you have to click the install icon on the desktop. and follow the prompts.

---

### Post by co.link on 2007-10-28
The reason I want to send a complaint is that I want Ubuntu to succeed.  I don't like Microsoft.  We need competition.  So far Ubuntu is the only operating system that I'm aware of that's seriously trying to compete for the PC market.  I don't see it succeeding if it fails the most important step of the process, easy installation.  Because of Ubuntu's market position, you really really really need to be able to install it anywhere and just have it work.  If it can't do that, many of us are going to get frustrated and just conclude that there isn't any point to try.

Right now I'm wrestling with whether I really care enough to keep trying.  I use the PC mostly for internet and word processing (Which I could use Ubuntu to do), but I do game, so I can't ditch windows yet.  I'm wasting hours of time trying to get something working that I may hardly, if ever, use.  I'm fairly good with computers, too.  Right now I have to tell my friends to avoid it, because the only way it seems to work is if you give it control to repartition your hard drive, which may cause you to lose your system files.

And yes, I did install it.  I read a lot of articles and went through a lot of threads before starting, which is another reason why this is so frustrating.  If I can't get this thing working in the next couple days, that's it for Ubuntu until the next version comes out.  I'll just go back to suggesting people leave it alone.  It's just not ready.

So...  why doesn't it boot when I Make '/' the boot partition, and what do I need to do to get this running?

---

### Post by oilchangeguy on 2007-10-28
gee, if it's not ready, then how is it possible that so many have had no problems setting up a dual boot? myself included. like i said it's not the operating system, it's the operator. since no one can see what you've done, it'll be hard to say just what you've done wrong. but don't blame the operating system (any operating system) for your failures.

---

### Post by logos34 on 2007-10-28
the active/boot flag (*) only matters for windows, afaik...I don't think that's the issue here.

Do the most obvious thing first: try [reinstalling grub from live cd]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by co.link on 2007-10-28
I'll give it a try, logos.  Thanks

Oilchangeguy,  All I did is this
1. install windows on the first partition, which is ntfs
2. Created extended partition with logical drives /, /home, swap, all of type Ext3 (as per previous suggestion by another forum person)
3. Installed Ubuntu to those partions

Dual boot didn't load, so I tried turning the boot flag to / and then /home.   It still didn't boot, so I put it back.  That's all I've done.

---

