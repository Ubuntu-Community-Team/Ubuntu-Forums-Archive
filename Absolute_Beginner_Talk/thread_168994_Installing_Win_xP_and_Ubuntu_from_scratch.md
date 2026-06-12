---
title: "Installing Win xP and Ubuntu from scratch"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by idontknow9999 on 2006-05-01
I never installed windows before on a partition... Here is what I am going 2 do:

1. Add my sata2 hdd to my comp.
2. Boot from floppy with fdisk.
3. Tell fdisk to assign 3 partitions (one for xp, one for ubuntu, one for vista later).
4. Install win xp.
5. Then install ubuntu
6. Setup dual boot screen (also got a floppy that I can do that with)

My question is: Windows xp format its partition, and makes it NTFS. What about ubuntu? Will I need to tell fdisk to make a specific type of partition? Also, am I missing anything obvious?

---

### Post by Sandlst on 2006-05-01
I would use fdisk to make a partition for XP and Vista, and leave the leftover space un-partitioned, using the 'Manual Partition Drives' during the ubuntu install to select the empty space.  Im not sure if fdisk can make it, but if it can the partition type would be Ext3 (unless you want it to be something else: you might try searching this forums for alternate filesystem types to find out if something would work better for you) also, if you do not have a ton of memory (or if you do and want to be safe) its a good idea to make another partition during the ubuntu install and set it to use as SWAP, make it ~2x your memory.  O yes, in order to set the ext3 partition select "Use as Ext3 Filesystem" during manual partitioning, it should automatically set the mountpoint to '/' which is what you want.  Post back if you have any problems.  

During the ubuntu install, it should detect windows already installed, if it pops a message up telling you it did, you will be able to choose which OS to boot into after turning on your computer, but it will boot by default into ubuntu in something like 15 seconds, so you will want to make sure you are sitting down ready to select it if you want to boot windows.

---

### Post by Jason_25 on 2006-05-01
I wouldn't go that way.  First, I wouldnt trust a floppy disk to format my drives.    Put your hard drive in, install xp, but DON"T do the default xp install.  make a C: partition of whatever size you want to use for windows with the windows installer (with the c button I think).  Then you'll have a C: with windows and a bunch of unpartitioned free space (hopefully) for ubuntu.  Now finish the windows install.  Now boot from the ubuntu install disc and install ubuntu like normal.  It will install grub to the master boot record and add xp as a boot option.

---

### Post by Papa-san on 2006-05-01
I agree with Jason... Sounds like the best bet for a simple dual boot system...

---

### Post by nalmeth on 2006-05-01
But you know that if you want to share files between the two, you'll have to make your windows fat32. The windows installer won't install fat32, but you can create one before hand, and tell windows to install into that.
Or you could use the third space as a fat32 share for both windows and ubuntu.

---

### Post by catlett on 2006-05-01
Don't make it so difficult.
Put in the XP install disc and boot into it. Let XP format the whole drive and install. You'll end up with 1 partition and the file system will be NTFS.
Next put in the Ubuntu install disk. Boot into that. Get to partitioning. Choose "resize existing partition and install". Ubuntu will shrink the windows partition. It will then format the space. It will make a SWAP partition amd an EXT3 partition for the file system. 
The Ubuntu install has a bootloader GRUB (grand unified bootloader) the pretentious name aside it does a great job. It will recognise Windows and will give you a boot screen where you can choose windows or Ubuntu.
By the time Vista comes out you should know Ubuntu good enough. In Ubuntu there is a partitioning app "gparted". You can use this to make a partition for Vista. Partition out ar least 10gb from the Window install and format it NTFS or Fat32. This is just to be safe. Vista should be able to recognise it no matter what but you never know with windows. Vista will ask you to overwrite XP or install 0on another partition. Choose the one you made and Vista wil install.
Now the problem. Vista will erase Gruib and install the windows bootloader. It will only recognise XP and Vista. YOu won't have an Ubuntu optiuon. Hopefully by then you will find out how to reinstall Grub. It never works for me, I always end up reinstalling to get grub back. God luck.

P.S. There are ways to access your NTFS partition from Linux and to access your EXT3 from Windows, but the easiest way is to do what the previous post said. Make a Fat32 partition. This will give you a space to put data you want to access fron either os. You can use gparted once your in Ubuntu or use fdisk. Personally I still use Partition Magic from windows. If you don't have it you can get a free trial version from CNET download. This way after your installs you can go into xp, run Partition Magic, make 2 partitions, a Fat32 common one and a vista one and your all done.

P.P.S. In case you're interested later, here is the driver for windows let lets you see EXT2 (and can be tweaked for ext3) file systems in windows [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) 
And this is the way to mount NTFS partitions in Ubuntu [http://ubuntuforums.org/showthread.php?t=142481&highlight=ntfs](http://ubuntuforums.org/showthread.php?t=142481&highlight=ntfs)

---

### Post by Ozitraveller on 2006-05-01
There is Dual Boot link below that might also help you. Windows/dos fdisk won't help you with linux paritioning.

I also agree with the above that a FAT32 partition is a good idea if you want to share data.

This is how I arrange my partitions when I re-build, it might give you some ideas. I have 2 hd's

hda (20gb)
Partition
#1 100mb  /boot bootable ext3
#2 19.9gb  /                   ext3 (root)
#3 1.0gb   swap              swp  (swap space 2 x ram)

hdb
#1 30gb    /home             ext3

It's simple, that's why I use it. There is more  you can do if you wnat to isolate multiple users on a workstation.

"if you want to use XFS, you should install GRUB to a separate /boot partition formatted with a different file system (ext3 will work fine). "
[http://distrowatch.com/weekly.php?issue=20060501#tips](http://distrowatch.com/weekly.php?issue=20060501#tips)

---

### Post by elamericano on 2006-05-01
Ozi,

That was good advice. I plan to do more partitioning for my next install, but I'm wondering why not use a swap file instead of a swap partition. I've been told there's no reason to use a seperate partition for swap anymore.

---

### Post by catlett on 2006-05-01
I didn't know Linux could use a swap file. I though Linux needs a swap partition and it was only windows that used a swap file. If it is possible and it works for you, please post because it will be something new for me.

---

### Post by Jason_25 on 2006-05-01
[QUOTE=catlett]I didn't know Linux could use a swap file. I though Linux needs a swap partition and it was only windows that used a swap file. If it is possible and it works for you, please post because it will be something new for me.[/QUOTE]
Search the forum.  Plenty of threads on it.

---

### Post by elamericano on 2006-05-01
The swap file is a fixed size, just like your partition, but if you wanted to change the size later, it's a bit more flexible.

> sudo dd if=/dev/zero of=/var/swapfile bs=1024 count=*memory-size-in-1k-blocks*
sudo chmod 600 /var/swapfile
sudo mkswap /var/swapfile
sudo swapon /var/swapfile
And then you add it to /etc/fstab:
> /var/swapfile swap swap defaults 0 0

---

### Post by catlett on 2006-05-01
Well here it is. I should spend more time researeching things about my system I guess. It's right here in the wiki.[https://wiki.ubuntu.com/SwapFaq?highlight=%28swap%29%7C%28file%29](https://wiki.ubuntu.com/SwapFaq?highlight=%28swap%29%7C%28file%29)
Here's an excerpt from the swap wiki.
6- How do I add more swap?

    *

      Usually, people associate swap with swap partition, maybe because they've been proposed to create a swap partition on install. In fact any file can be used as a swapping device, be it a partition or a conventionnal file.
    *

      It's true that swapping to a real partition is faster than swapping to a file, but not that faster. If you're considering responsiveness, my advice: add more ram. Swapping to a partition or a file won't change anything.
    *

      We will add more swap by adding a swap file.
    *

      Adding more swap is a four-step process :
          o

            a- Creating a file the size you want.
          o

            b- Formatting that file to create a swapping device.
          o

            c- Adding the swap to the running system.
          o

            d- Making the change permanent.

---

### Post by catlett on 2006-05-01
[QUOTE=elamericano]The swap file is a fixed size, just like your partition, but if you wanted to change the size later, it's a bit more flexible.


And then you add it to /etc/fstab:[/QUOTE]
Sorry to steal the thread but thanks for the insight. I never new that but thanks to you now I do. Regards. Catlett

---

### Post by idontknow9999 on 2006-05-02
[QUOTE=catlett]P.S. There are ways to access your NTFS partition from Linux and to access your EXT3 from Windows, but the easiest way is to do what the previous post said. Make a Fat32 partition. This will give you a space to put data you want to access fron either os. You can use gparted once your in Ubuntu or use fdisk. Personally I still use Partition Magic from windows. If you don't have it you can get a free trial version from CNET download. This way after your installs you can go into xp, run Partition Magic, make 2 partitions, a Fat32 common one and a vista one and your all done.

P.P.S. In case you're interested later, here is the driver for windows let lets you see EXT2 (and can be tweaked for ext3) file systems in windows [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) 
And this is the way to mount NTFS partitions in Ubuntu [http://ubuntuforums.org/showthread.php?t=142481&highlight=ntfs](http://ubuntuforums.org/showthread.php?t=142481&highlight=ntfs)[/QUOTE]

I cant have a fat32.... I got 448.95 GB of data in NTFS...

Here is my setup:
200 SATA 2 (this will be my main, installing it tonight or tomorrow)
250 (NTFS) GB IDE - movies drive. ~15 GB left
250 (NTFS) SATA 1 - Data, application, games, documents, etc. ~1 GB left

Linux needs to have the ability to read and write in NTFS.

---

### Post by Ozitraveller on 2006-05-02
As far as I know Knoppix is the only distro handle NTFS correctly. But I could be wrong, and there could be others. ;-)

I hadn't seen that info before, on swap files! Interesting, thanks. ;-) But, resizing a partition isn't that difficult either, GParted:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by physcsdrk on 2006-05-02
You may have a problem tripple booting with vista: 


[http://www.theregister.com/2006/04/27/schneier_infosec/]("http://www.theregister.com/2006/04/27/schneier_infosec/")

---

### Post by Ozitraveller on 2006-05-03
[QUOTE=physcsdrk]You may have a problem tripple booting with vista: 


[http://www.theregister.com/2006/04/27/schneier_infosec/]("http://www.theregister.com/2006/04/27/schneier_infosec/")[/QUOTE]

Yes, but vista is at least 2 years away and hopefully this will be resolved by then. ;-)

---

