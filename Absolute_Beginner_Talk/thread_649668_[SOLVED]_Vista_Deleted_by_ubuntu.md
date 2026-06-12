---
title: "[SOLVED] Vista Deleted by ubuntu"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by luvlinux on 2007-12-25
hello! I have a problem with ubuntu/vista.
when i installed ubuntu i had Windows vista on my computer and when i rebooted it vista was gone!!!! :confused: I logged in to ubuntu and rebooted my system and the menu of wich operating system i want to choose came. But vista was not there! :( so i started in ubuntu and saw that there was 182GB of harddrive left, but before i installed ubuntu i had like 40GB left of 200GB. I just want my files and vista back! please anyone help me!!!!!!!

sorry for my english,

---

### Post by foo25 on 2007-12-25
Do you remember how exactly you partitioned your hard drive? Using the whole 200GB or the largest free space, or perhaps another option?

---

### Post by bumanie on 2007-12-25
The only that comes to mind is to download the live cd of test disk. It has a good chance of recovering your vista partition.

---

### Post by gfg on 2007-12-25
You probably chose to use the entire harddsik during install, thus you deleted your vista partition. If that is the case, ubuntu didn't delete vista, you did.

---

### Post by rye_ on 2007-12-25
This is great news.
It seems that Ubuntu is capable of recognising and deleting cr*p from a users HDD upon  installation.

Couldn't help myself :)

Ryan

---

### Post by Sef on 2007-12-25
Let's see if Vista is there or not.

Applications > Accessories > Terminal

type in 

```
sudo fdisk -l
``` (small L)

paste the results here.

---

### Post by luvlinux on 2007-12-25
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38157   306496071   83  Linux
/dev/sda2           38158       38913     6072570    5  Extended
/dev/sda5           38158       38913     6072538+  82  Linux swap / Solaris

---

### Post by luvlinux on 2007-12-25
> **bumanie said:**
> The only that comes to mind is to download the live cd of test disk. It has a good chance of recovering your vista partition.


what is the "live cd of test disk" and where can i downnload it?

---

### Post by tibellus on 2007-12-25
As I can see from your output, it seems you've set Ubuntu to use the entire disk. Unfortunately, it was formatted, but I think there are some programs out there for recovering files, even after a format. It is a tedious process, but if you have some important files, I'm pretty sure you'll wait for it to finish.

---

### Post by bumanie on 2007-12-25
Test disk is a live cd that is basically a data\partition recovery tool. got here [www.cgsecurity.org/wiki/TestDisk](www.cgsecurity.org/wiki/TestDisk) or here [www.cgsecurity.org/wiki/TestDisk_Download](www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by foo25 on 2007-12-26
As tibellus said, you must have chosen to format your whole hard drive and wipe Vista. There is a chance that the files still exist, but it is quite likely a lot of them would have been overwritten by the Ubuntu installation. Ubuntu did not wipe Vista, you told it to, unfortunately this happens quite often I'm sure with first time users, and I can only hope it doesn't put you off. I did it myself when I started using Ubuntu 6.06, even after trying it on a separate hard drive first.

To be honest you could try to recover those files using the Test Disk posted above, but if your Vista partition didn't contain anything too important, I'd start over. Use your Vista disk to make a partition big enough for Vista and your files, or even a few separate partitions, ie. one for Vista itself, one for personal files, one for downloads. I did that on my laptop and it helped greatly as if Vista gets damaged and you need to reinstall you don't loose all your files. Once that's done, don't forget to leave some free space for Ubuntu and it's swap file.

Although it sounds complicated perhaps, it's really quite easy. Best to use NTFS filetype for Windows, and then ext3 for your Ubuntu installation, but that will be chosen by the installation itself, just make sure to choose Largest Free Space, or a similar option to insure you do not wipe any data. Hope this hasn't put you off Ubuntu, it's well worth trying, and I'd recommend you try the above and give it another go.

Good Luck!

---

### Post by Lord DarkPat on 2007-12-26
I'm terribly sorry, but it looks like you have wiped your hard drive and installed ubuntu. You should have chosen manual partitioning.

---

### Post by tibellus on 2007-12-26
I think everyone did this mistake. Don't worry - unless you had very important information on that partition -, you can now start from zero. But, as far as I know... If you want to install Vista or other Windows, it will ruin the bootloader, if you install it AFTER you've set up Ubuntu (or other distro).

---

### Post by luvlinux on 2008-01-03
well i just installed Vista again and i think i will use that from now.
Ubuntu was a little to advanced for me and i mostly use my computer for gaming. My internet card did not work eighter in ubuntu and i had a "Linux Geek" to come and take a  look at it, and he sat and typed commands and stuff in the terminal window to an hour and still coud not find the error. So from now on i will use a slow, unreliable, closed, expensive system with 112438 viruses threatening you all the time and endless security warnings.:D
Thank you for all for your good comments and help, exept you, rye_  ;-)

---

### Post by Fixman on 2008-01-03
NOTE THAT this process its very difficult, unless you had very important files in there, I just reccommend you to re-install vista, that DOES wipe out everything. You must use gParted to do a partition anyway.

---

### Post by Arkaniad on 2008-01-03
Whatever Kill Vista

---

