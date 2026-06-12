---
title: "Tripleboot Ubuntu, Arch and Windows 7"
date: 2011-10-05
forum: Any Other OS
---

### Post by Wintus on 2011-10-05
Hello,

I bought a Thinkpad x61s a few days back and thought about making it into a "linuxlaptop". My plan is to install Ubuntu, Arch Linux and Windows 7 into tripleboot and to make an ntfs-partition for common use (music, documents and stuff). For clarification, Ubuntu as a friendly, easy-to-use linux and Arch as a learn-to-do-stuff linux. My problem is the partitioning. I have a 160gb drive and I don't know how should I partition it. I googled around and something about installing the linuxes into the same home directory came up. Also, I have no idea which OS I should install first and and the bootloader is giving me creeps. I know I should propably make an "extended drive" or something (google brought this up too..) to make so many partitions but once again, I have no idea.

I have Gparted burn into usbstick, and technically I can do the partitioning. I just don't know how I should do it. :/

Don't kick my *** too much if I posted this to a wrong sector, because I think I propably did. :)

---

### Post by ajgreeny on 2011-10-05
What is your current partition setup?  You can only have 4 primary partitions on a disk, or 3 primary and one extended which itself can hold many logical partitions.  To show how you have the disk at present I suggest you run gparted and send us a screenshot of what that shows, or if you already have the ubuntu live CD, boot to that and use gparted from the live CD.  You could also run the command ```
sudo fdisk -l 
```in a terminal and copy here the output from that.

Windows OS partition must be a primary partition or it will not boot, but linux can be on logical partitions without a problem.  Therefore the best way I suggest to do what you want is to have windows installed first, which I assume you have already got.  Unfortunately windows 7 often is installed using all the maximum of 4 partitions available on a disk, hence my question.

From your answers to the above, we will be more able to suggest a sensible partition layout for you.  However, to answer one query straight away, you can not safely use the same /home folder for both Arch and Ubuntu without causing potential problems, though you can have different /home folders for each OS in the same partition.

---

### Post by oldfred on 2011-10-05
Welcome to the forums.

I do not know Arch nor Win7, but will offer a suggestion, others may have something slightly different.

I understand Windows needs 30GB+ depending on what you install. If most data is elsewhere you may not need a lot more. NTFS partition really need 30% free space so do not make Windows too small. 

I have multiple Ubuntu installs and use 20-25GB for / (root) but have all data in other partitions. Some data is in my old shared NTFS (with XP) and now most is in a shared ext3. But that only works since all systems are Ubuntu and there are no UID/GID user/group issues on ownership. Same UID/GID issues as well as software version differences make sharing a /home not a good suggestion. If you have most data in your shared NTFS partition /home does not have to be large. My /home (still in /) is about 1GB with 3/4s of that as .wine with Picasa as wine is more difficult to move. But I move all data folders and some hidden folders with data like Firefox & Thunderbird profiles to the NTFS shared so I have all the same email & bookmarks in all systems.

Window has to have a primary partition, so I would install it first. I would install everything else in logical partitions, so you leave the primaries available in case you want them later. You can share swap as long as you do not hibernate.

---

### Post by SirDrexl on 2011-10-05
If you're able to wipe the drive, what I like to do is create partitions as I go, instead of doing them all at once.  Install Windows, which will create two primary partitions (one 100MB system reserved and one for Windows itself), and leave the rest unallocated.  Then do the same for each Linux distro, using extended partitions, and then finally format whatever is left as the storage partition (do this within one of the newly installed OSes).

But, you would need a Windows disc which probably didn't come with your laptop.

---

### Post by perspectoff on 2011-10-05
Not everyone likes my methods (because they are very simple and prone to long-term stability, which not everyone in IT likes these days), but I have been using these methods for a long time to have many, many OSs on my computers:


[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

---

### Post by Wintus on 2011-10-05
Thank you for quick responses.

My current partitioning is... quite a mess, so I was thinking about wiping it all clean. And I do have a Windows disk, bought separately.

So if I understood you correctly, I should now install Windows on a primary partition. I may install some programs, maybe a game or two (the oldies but goldies, I have a PC for "hc-gaming") so I should use around 40gb for it to be sure? Then install Ubuntu and Arch to a logical partition, and make it, umm, 20-30gb? Then swap of course, and after that make the storage partition. Correct me if I'm not following. :)

---

### Post by hyper2hottie on 2011-10-05
Personally I would never install Windows in a partition smaller than 60gb, and that is a bare minimum.  Windows bloats really fast even if you don't use it alot.  If you want to game from that windows then your going to need an external drive for your games or something like that.  

With that said, for your machine I would give Windows at least 60gb, Ubuntu around 30 GB, Arch I have never used by I would say no less than 20GB.  That leaves 50GB for your media partition.  You can change these for your own needs, but this is what I would do.

---

### Post by zhogan85 on 2011-10-05
Since you are going to have a shared data partition, you'd be fine with 20 gb for both arch and ubuntu (I have mine set up like that, also with a shared data partition). I cannot speak to the size of your windows partition.

---

### Post by mips on 2011-10-06
Whatever partitioning scheme you decide on install Windows FIRST!

If you install it after you have installed any linux distro it will overwrite GRUB.

---

### Post by Wintus on 2011-10-13
Little late but anyway, did it and it's working. Thx everyone :)

---

### Post by viperdvman on 2011-10-13
I agree with most everyone here. But for me, I would allocate 50GB to Windows 7, 20GB to Ubuntu, and 20GB to Arch. That's the really nice thing about any Linux, they take up less than half the space that Windows takes up... and that includes all the apps installed with those OS's.

I only run a dual-boot on my netbook. But I have 100GB for Win7 (factory default), 20GB for Ubuntu, 16GB for my Win7 Restore partition (factory default), and the rest for data, media, etc. that both OS's can access. And I have a 250GB hard drive.

Good luck with your setup :)

---

### Post by zhogan85 on 2011-10-13
> **Wintus said:**
> Little late but anyway, did it and it's working. Thx everyone :)

Good to hear! How do I like Arch? I'm new to it as well, and installed it for the same reason as you. I really like it, I've ran into some hiccups along the way, but I'm getting pretty close to my ideal setup in Arch (using openbox).

---

