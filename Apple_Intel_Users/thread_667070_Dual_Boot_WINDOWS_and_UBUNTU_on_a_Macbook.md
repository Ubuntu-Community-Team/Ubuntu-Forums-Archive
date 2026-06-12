---
title: "Dual Boot WINDOWS and UBUNTU on a Macbook"
date: 2008-01-14
forum: Apple Intel Users
---

### Post by FunnyLookinHat on 2008-01-14
So here is my goal.

Boot ONLY Ubuntu and Window...  Not OS X.

Let's be frank.  OS X is pretty crappy and I have NO use for it.  The only reason I want windows is to run World of Warcraft.  I don't have enough hard drive space to triple boot.

So I was wondering, if I make two primary partition (one for ubuntu and one for windows)... will my bootloader (reFit) recognize those installs automatically?  Or do I have to do something special with it so that it will recognize the operating systems I have installed.

Thanks guys!
-David

---

### Post by tommy1987 on 2008-01-14
Out of interest, if you believe that then why pay out excessive amounts of money to even have an Apple computer?

---

### Post by cyberdork33 on 2008-01-14
> **tommy1987 said:**
> Out of interest, if you believe that then why pay out excessive amounts of money to even have an Apple computer?This is not conducive to the forum nor the question. Your opinion may be different, but it is not relevant to the discussion.

> **FunnyLookinHat said:**
>          So here is my goal.

Boot ONLY Ubuntu and Window...  Not OS X.

So I was wondering, if I make two primary partition (one for ubuntu and one for windows)... will my bootloader (reFit) recognize those installs automatically? Or do I have to do something special with it so that it will recognize the operating systems I have installed.

You can certainly dual boot only Windows and Ubuntu, but there a few things that you should know before you do so.[LIST=1]
[*]Without OSX installed somewhere (even an external drive), you cannot get firmware updates for your system.
[*]rEFIt has a configuration file that is stored on the OSX partition. While I do think it will operate just fine without it, just keep in mind that you cannot change any of the options in it anymore. (It may be possible to put the rEFIt files on another partition, but I am not sure how this would work. It might be best to direct an inquiry to the rEFIt developers). Also, keep in mind that you can only reinstall rEFIt with OSX since all the utilities are OSX commands. (specifically, the bless command).
[*]It may be worthwhile to consider reformatting the entire drive to a standard MSDOS / MBR Partition table instead of the GUID partitioning system that the Mac uses by default. This will allow Windows to access a much greater number of partitions, and you do not have to deal with syncing tables nor concerning yourself with making sure certain partitions are in certain locations.[/LIST]

---

### Post by ramvi on 2008-02-19
@tommy1987: They're sexy.

@FunnyLookinHat: I'm doing this. I havent tried with refit though. Just format the whole drive using gparted (change disklable to msdos) and use the computer as any other computer. grub for choosing windows / ubuntu

---

### Post by doorknob60 on 2008-02-20
> The only reason I want windows is to run World of Warcraft

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

:) Why even bother with Windows?

---

### Post by ronocdh on 2008-02-22
> **doorknob60 said:**
> [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

:) Why even bother with Windows?
I'm really glad someone posted this. This bears repeating, because as much as people rip on gaming on Linux, there are some really smooth experiences out there. Understandably, they're usually with the most heavily played games, as more people are interested in getting them running, but not always.

Anyway, please check this guide out, Funny, if you're really just keeping Windows for WoW.

---

