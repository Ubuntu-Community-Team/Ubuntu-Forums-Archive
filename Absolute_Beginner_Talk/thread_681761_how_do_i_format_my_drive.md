---
title: "how do i format my drive"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by benniebrown07 on 2008-01-29
I have a hard drive with Ubuntu (80gb) and i have one with Mandriva (40gb). I wanna format the one with Mandriva and install windows. I like Linux more than windows but i cant burn dvd's and play games. When i put the xp cd in it stops (black screen) when it first comes on then i hear the dvd drive then after a couple secs Ubuntu starts up, its like xp is trying to install. How do I go about doing this correctly?

---

### Post by jan quark on 2008-01-29
when you search formating documentations
I have created a list with the important ones there you find the most important information
[http://janquark.fatfreehost.com/partitions.html](http://janquark.fatfreehost.com/partitions.html)
you format with the application gparted

---

### Post by benniebrown07 on 2008-01-29
if i reformat the drive with mandriva when i put the ubuntu drive back in itll still work right? will i still have my drivers (not sure if the words drivers but>) you know the things I need to run my dvd burner, software and stuff ?

---

### Post by jan quark on 2008-01-29
if you have two completely independent separate drives or partitions I see no problem in formating the mandriva partitions,

but I dont wanna tell you something and the your PC is trash, wait for someone more experienced to answer

but when you think of installing windows after ubuntu, there might be some issues with the dual booting becuase windows ( xp and vista as far as I know, and perhaps also the older versions) overwirte the grubloader. so you have to restore the grub loader manually.
but there are also documentation on the internet how to do this

here is a good site for dual booting
[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by zvacet on 2008-01-29
Read [this](http://ubuntuforums.org/showthread.php?t=179902).Maybe that can help you.

---

### Post by Ex-windows on 2008-01-29
Did you set your bios to boot from the cd rom?

---

### Post by bodhi.zazen on 2008-01-29
> **benniebrown07 said:**
> I have a hard drive with Ubuntu (80gb) and i have one with Mandriva (40gb). I wanna format the one with Mandriva and install windows. I like Linux more than windows but i cant burn dvd's and play games. When i put the xp cd in it stops (black screen) when it first comes on then i hear the dvd drive then after a couple secs Ubuntu starts up, its like xp is trying to install. How do I go about doing this correctly?

When you boot the windows disk it will do everything for you, including formatting.

I second Ex-windows's thought, your problem is booting the windows disk and not formating.

To answer your question though you can format a partition with gparted or from the command line. See this link for commands : 

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

(scroll down to the bottom of the first post).

and this for gparted : [Documentation](http://gparted.sourceforge.net/documentation.php)

And, you recall, you will need to re-install grub after installing windows :twisted:

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by benniebrown07 on 2008-01-29
so far ive ran the g parted software and the partition is there and now ill install xp thanks for the help so far but i may still need help

---

