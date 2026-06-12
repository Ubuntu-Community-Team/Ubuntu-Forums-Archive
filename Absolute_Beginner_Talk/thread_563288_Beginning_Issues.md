---
title: "Beginning Issues"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by Loser777 on 2007-09-29
I recently installed Ubuntu, after many problems dealing with partitions. (I'm dual booting with XP)  However, now that I'm over that hill, I'm facing new problems.
I managed to install WINE with zero Linux knowledge, but I'm having trouble running StarCraft.
StarCraft starts fine and games run fine, but problems happen when I try to go on bnet.
The Connecting to Bnet screen displays in an odd font for around 2 seconds, and StarCraft crashes.
I've heard that this is because of some font metrics issue, but I don't know a solution.

Aside from that, I'm trying to install the official Nvidia Linux drivers for my 7600GT and Beryl ;).
I have no clue how to install Beryl and I'm getting a character encoding error when running the driver installer's .run file.

Anyone know anything that might help?

---

### Post by overdrank on 2007-09-29
> **Loser777 said:**
> I recently installed Ubuntu, after many problems dealing with partitions. (I'm dual booting with XP)  However, now that I'm over that hill, I'm facing new problems.
I managed to install WINE with zero Linux knowledge, but I'm having trouble running StarCraft.
StarCraft starts fine and games run fine, but problems happen when I try to go on bnet.
The Connecting to Bnet screen displays in an odd font for around 2 seconds, and StarCraft crashes.
I've heard that this is because of some font metrics issue, but I don't know a solution.

Aside from that, I'm trying to install the official Nvidia Linux drivers for my 7600GT and Beryl ;).
I have no clue how to install Beryl and I'm getting a character encoding error when running the driver installer's .run file.

Anyone know anything that might help?

HI and welcome, I can not help with the wine questions but have you tried to enable the restricted drivers located under, system, applications, restricted driver manager? If you continue installing official driver you will have to do it again at the next kernel update. You may have a look at Envy also [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)  But by all means search the forums and see what would be best for you. You can use this thread for beryl and Comp-fusion
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)
Ignore the ati drivers of course just the commands for Beryl. Good luck!

---

### Post by Loser777 on 2007-09-29
Thanks for the help, but now I've run into another problem. My linux partition was only 5GB, so now I only have 121MB of free space. What should I do?

---

### Post by st33med on 2007-09-29
Download and burn the [Gparted LIVE CD]("http://gparted.sourceforge.net/livecd.php") as an image.
Back up your files, just in case.
Boot from the CD.
Shrink your NTFS partition (that is the Windows partition) to less than half of it's current space. Otherwise, Windows won't boot.
Increase your EXT3 partition (your Ubuntu partition) to fill up your empty space. Continue.

---

### Post by Loser777 on 2007-09-29
I have to shrink it to half of its normal size? I have 30GB left of space which isn't defragged.
My windows partition is like 130GB/ 100GB used.

---

### Post by rickycodie on 2007-09-29
try winedoors it automatically configures wine and from there has a very nice package manager.

[http://www.getdeb.net/app.php?name=Wine-Doors](http://www.getdeb.net/app.php?name=Wine-Doors)

---

