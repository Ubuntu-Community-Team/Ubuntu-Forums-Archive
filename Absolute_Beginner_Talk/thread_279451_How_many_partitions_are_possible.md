---
title: "How many partitions are possible?"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-18
I was thinking about trying a comparison triple boot:

is this possible in 60gbs:

Windows:33gb

xubuntu 6.06:15gb
swap:1gb

ubuntu 6.06:10gb
swap:1gb

Would I get a better comparison of the difference between GNOME and XFCE and their apps if they were both installed on different partitions than if they were on the same partition.

And if it doesn't matter if they are on the same partiton, then would it be possible to have this on the 60gb:

Win:33gb

xubuntu 6.06 and ubuntu 6.06:15gb
swap:1gb

xubuntu 6.10 Beta 1:10gb
swap:1gb


Do I need a swap for each partition if this possible?

Hopefully these are my last questions for a while.

thanks,
-c.

---

### Post by gustolove on 2006-10-18
The Linux installations can share the Swap partition. there is no reason for 2 swaps.

The apps should work fine if they are on the same partition whether u are in gnome or xfce. they would probably both be the same file system any ways right?

---

### Post by aysiu on 2006-10-18
In answer to your original question, you can have four primary partitions. I'm not sure what the limit is on extended partitions.

And don't ask me what the difference is, either, as I don't know.

---

### Post by crimesaucer on 2006-10-18
I was interested in comparing overall quickness of browser surfing between the two, quality of default or suggested media players or how fast and easy the default apps like the terminal and text editors were in comparison to each other.

I mean so far, from what little time I've spent on the both, I like the fastness of xfce and xubuntu, but the ubuntu looks like a lot easier of a file system. I would love to find out how the suggested packages compared to one another and how shared packages like VLC or wine worked on each system. If they can be compared side by side, on one partition, then cool, because I would love to have a beta 6.06 to mess around with and try to learn xubuntu through observing developer errors and error fixing. It seems like a quick way to learn.

---

### Post by pay on 2006-10-18
You can install Gnome (Ubuntu Window Manager) and XFCE (Xubuntu Windows Manager) on the same install. To install either just open the terminal and type```
sudo aptitude install ubuntu-desktop
```or```
sudo aptitude install xubuntu-desktop
```

---

### Post by DTXBrian on 2006-10-18
*ACTUALLY...* since you asked a specific question... there is a limit of any combination of 4 Primary partitions and Extended partitions... but there's only a real need to have 1 Extended partition if you make all of your logical partitions adjacent.  They'll all coexist in the same Extended partition then.  You may have an infinite number (within reason, considering your HDD's size) of Logical Partitions.

---

### Post by crimesaucer on 2006-10-18
I read your post a little too late, and installed and upgraded my first install. For my next install of the beta, could you explain a bit on how I could creat an extended partion. I also was wondering since I installed the xubuntu desk top on top of the ubununt, no matter which desktop I choose, I will have the same packages, right.

thanks,
-c.

---

### Post by Bachstelze on 2006-10-18
Yes, a Desktop Environment is basically a piece of software like any other. Different DEs do **not** necessarily make different distros.

About the primary/extended thing, an extended partition basically allows you to have as many partitions as you want. You can only have four primary partitions max., but you can also have three primary and one extended, the extended containing as many logical partitions as you wish. To create one during Ubuntu install, just create a Logical partition instead of Primary, it will automagically create the extended partition if you don't already have one.

---

### Post by xpod on 2006-10-18
I have kubunto desktop installed on an ubunto install and both lots of apps show up in both desktops menu`s..

I think you might come across some that might need enabled or similar to show in the menu`s but that happens with a plain single desktop in my experience anyway...which aint much.

I also use the "debian menu" which is great for showing all installed apps but generally if somethings missing from a menu you can usually enable it in the relevant menu editor or just start the app from the terminal\konsole etc.

---

### Post by Bachstelze on 2006-10-18
Or add a launcher to the menu yourself ;)

---

### Post by randiroo76073 on 2006-10-18
Is that 4 total, what if you have multiple hdds, I currently have 3, do I get 4 primaries per hdd or just 4 for 3 hdds

---

### Post by Bachstelze on 2006-10-18
Not 100% sure but it's 4 primary partitions per drive I think. Otherwise, what if you had five drives ? :p

---

### Post by ReaderRat on 2006-10-18
I believe only Primary partitioms are bootable.

---

### Post by Bachstelze on 2006-10-18
Yep, forgot about that...

---

### Post by randiroo76073 on 2006-10-18
Hmm???  Now I am mixed up, grub allows you to boot from extended/logical yes?  So what you are saying is that grub will only recognize 4 primaries, period?  no matter the number of hdds?

---

### Post by Bachstelze on 2006-10-18
GRUB has nothing to do with it. You can only have four primaries or three primaries plus one extended per drive, whatever you use them for.

---

### Post by randiroo76073 on 2006-10-18
Aha,so, 3x3=9 primaries + 3 extended, + logical=you name it :)

---

### Post by Bachstelze on 2006-10-18
Maximum, yes. You can very well have drives with just one partition if you want.

---

### Post by Bartender on 2006-10-18
How many are possible?
Check out this guy's project...
[http://www.justlinux.com/forum/showthread.php?t=143973](http://www.justlinux.com/forum/showthread.php?t=143973)

---

### Post by CatKiller on 2006-10-18
It's not a question of GRUB, it's a matter of the Master Boot Record method of organisation of an IDE hard drive. GRUB is sensible and can boot from any partition. Windows can only boot from an "active" partition, and only a Primary partition can be made active.

There is a limit to how many logical drives you can have per extended partition. I believe that it is 24. Which I think makes it 27 partitions per hard drive as a theoretical maximum.

---

### Post by randiroo76073 on 2006-10-18
Well that kinda answers that question, in a BIG way too :)

---

