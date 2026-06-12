---
title: "A list of minor annoyances....."
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Catsworth on 2007-02-12
Hi Guys,

Ok, I'm not exactly sure what's going on here, but I'm starting to wonder if a whole load of things that have suddenly gone wrong might be connected somehow:

1.  [BlueJ has stopped working](http://www.ubuntuforums.org/showthread.php?t=357361)
2.  [My Ubuntu install is running (or, at least, hanging) on fsck at every boot](http://www.ubuntuforums.org/showthread.php?t=358633)
3.  My grub menu has changed, I now have two versions of the Linux kernel listed [1]
4.  My screensaver no longer works, the screen just goes blank when the time runs out [1]
5.  [Connection Manager has stopped connecting to my preferred wireless network automatically](http://www.ubuntuforums.org/showthread.php?t=299462&page=56)


And that's just the things that I know about, every day I find something else that's gone wrong and it's starting to get more than a little frustrating.

I've read that other people have had problems with the new kernel screwing things up, is it possible that it's caused all these things to go wrong on my system?
I'm considering a complete reinstall, but I've invested a lot of time and effort getting this far so that needs to be a last resort - besides, I thought that complete rebuilds were something I was going to be leaving behind when I left Windows.

Thanks for the help guys.

[1] Anything marked [1] I think I can fix myself, but I'm loath to do so at the moment because I'm getting tired of fixing one thing only to find that another two have broken.

---

### Post by Jussi01 on 2007-02-12
Hei, try booting with the older kernel  -  then see if the problems are still occuring, if they are not, you know its the new kernel. Alot of people had problems with it - see the blue/green post at the top of the forum..

---

### Post by jvc26 on 2007-02-12
Another brief note: Should you ever want to reinstall etc, or when installing a new version of ubuntu, its a good idea to store your /home on a separate partition, that way your files and settings are preserved across the reinstall.
Il

---

### Post by Catsworth on 2007-02-12
/home (for all users) is already on a seperate partition.

Does this mean that if I reinstall _all_ of my settings will be retained (desktop wallpaper, wireless connection, programs I've installed)?

---

### Post by Foxmike on 2007-02-14
Desktop wallpaper would still be there as well as themes/icons you installed.  Setting for most applications will still be there, but applications themselves are stored elsewhere than /home so you will have to re-install your applications.

Concerning fsck, do you have a big (huge) hard drive?  I know that after a couple  disc mount operations (30 if I remember well) fsck will automatically chek file system upon boot.  This may take some time on big hard drives that uses ext2fs (no journal).  This is then normal.

The screensaver may be just a video driver thing.  Try re-installing your video driver (if you have any).

Hope it helps out!:)

-FM

---

### Post by Catsworth on 2007-02-15
Hi Foxmike,

Nope, don't have a particularly large HDD (it's 60Gb partitioned into 4).  It's not just doing the check every 30 boots, it's doing it all the time :(

---

