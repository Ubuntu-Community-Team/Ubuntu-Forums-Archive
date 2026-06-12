---
title: "Resizing NTFS partition to make room for Ubuntu"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by rrig004 on 2007-01-13
Hi 
I am planning on doing my first Ubuntu install on my laptop and have a question before I proceed.
I am planning on using the gparted live CD to partition my hard drive for a dual boot system and have defragmented my hard drive several times, but there are still a small group of files  in the middle of my hard drive, right were my ubuntu partition will be. So my question is will gparted relocate these files or they be losed.

I don't want to have to make my Windows partition any bigger and can't figure out how to move the files closer to front of the hard drive.

Any help would be appreciated.

---

### Post by bigken on 2007-01-13
I think they would be lost

---

### Post by cybrkup on 2007-01-13
I am no expert with Linux, but I had the same issue when I created a new partition on my windows drive to make space for ubuntu. Some files were seemingly stuck in the middle of my drive and wouldn't move no many how many times I defraged the drive. Bottom line, I used Gparted to create the new partition before I did the install and everything worked fine. I didn't lose any files. Of course, that may not happen for you so be sure to backup everything.

---

### Post by logos34 on 2007-01-13
Try disabling windows paging and hibernation files--that might be what's in the middle of the disk.  

Here's [a link]("http://www.linuxdevcenter.com/lpt/a/6554") that others have found helpful in resizing winxp on their laptop

---

### Post by goatflyer on 2007-01-13
I had a similar issue and what I did was the following overly-paranoid set of steps:

1) defrag everything. (which you have done)
2) boot a ubuntu live cd or puppy or knoppix - whatever you have.
3) open terminal, type:
```

  fdisk -l

```

... that's -l as in list.
4) copy down the start, end, block and type numbers for ALL partitions, not just the windows one.  Keep them in a notebook.  You are doing this in case you need to restore them manually.

5) exit that, reboot using the gparted cd.

6) use the gparted tool to shrink the windows partition only.  Gparted supposedly moves files around to make the shrink happen (which supposedly makes step 1 redundant, but you'll be glad you did step 1 if you have to manually restore things)   Do not create any new partitions yet!

  Also note: leave windows a reserve of at least 25% free space in the resized partition.  Windows does not work well with too little free space.

7) Exit gparted, reboot into windows.  Run scandisk, then defragment again for good measure.  Confirm for yourself that at this stage, windows is still happy living in the smaller partition.  If you and it are happy, go to step 8.

If for any reason, if you could not boot into windows, or if windows complained about anything, you can always restore your old partition data.  Here's how:  reboot into the live cd again, do fdisk -l again, you will see that only the 'end' value changed and 'blocks' were reduced.  In this case you would fdisk /dev/hda, then re-enter the end value.  Depending on the version of fdisk, you may need to "delete" the old partition and then "create" it again with the same "start" value.  Save partition table, exit, reboot into windows and all should be how it was before.

8) Ok, so windows is happy in the smaller partition, time to make your own. You could go back to gparted and do it from there, but the Ubuntu installation already contains gparted, so you could use that one during the install.

9) Install Ubuntu, when you get to the partitioning disk step, select 'partition manually'.

10) create a 2 or 4 GB 'swap' partition.  They say you should have double your physical memory size, but even a 512MB machine I would create a 2GB swap.

11) If you have the space and want to stay super-organized, create a /home partition for all your personal files, data, settings.  This way, even if you wipe out your new OS or install some other Linux, you'll retain all YOUR files.

12) Finally, create a '/' partition for ubuntu.  '/' is pronounced 'root'  This is the one to make bootable.  Tell the installer to install ubuntu here.

13) FInally, the installer wants to install grub to the MBR (master boot record) of your hard disk.  LET IT.  grub will detect your windows installation and create an entry for it.  Each time you boot your computer, you can select (with keyboard arrow keys) which OS to boot from.

14) finish the installation, and enjoy your dual boot system!

---

### Post by rrig004 on 2007-01-14
Thank you all for the advice, I feel a bit more confidant now about the proccess ahead.

---

### Post by migla on 2007-01-14
Maybe windows virtual memory has the pagefile somewhere at the end?

And a good idea would be to do check disk (or is it scandisk) (with all options marked) on the drive in windows **before** you resize, so bad blocks/sectors won't mess with the moving of files by gparted.

---

### Post by birdseye on 2007-01-14
I had exactly the same situation after doing a defrag, but it never occurred to me to worry about it. So I simply installed Ubuntu using the gparted tool to partition and everything worked fine. The only mistake I made was to leave the windows partition a bit small, given that I soon realised that switching over to Linux completely is not really realistic because of all the smaller applications you aquire that are windows only and dont work with wine.

So my message is to think carefully about partition size before you install

---

### Post by housam on 2007-01-14
Do the defrag once more and look for the unmovable data green mark(windows system files)where it is , because you can't partition the HDD before resizing it to just before that mark or you will damage windows.that means if it is located in the middle , your windows partition will be not less than the half of its capacity . leaving the rest of the HDD unallocated.
You can use Gparted tool to do the partitioning manualy before starting the installtion( it is in the live CD >> system >>.
During the installation process chose the manual partitioning to just put every thing in the right order.
You need to devide the unallocated part to three partitions :
- 10 - 15G ext3 /. for root
- 1G swap ( useless if more than 1G , you may not use it ever if you have 1G RAM or more.)
- The rest Gb is ext3 for /home
Good luck
__________________

---

### Post by bigken on 2007-01-14
I would run disc clean up and defrag in safe mode and also clean up the system restore points and use gparted liveCD to create the partitions

---

### Post by rrig004 on 2007-01-17
Thank you for the help, I have just installed ubuntu, but am now having a nother problem.
I have posted a new thread relayed to this problem [_[COLOR="DarkOrange"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?p=2024768#post2024768") and would really appreciated any help.

---

