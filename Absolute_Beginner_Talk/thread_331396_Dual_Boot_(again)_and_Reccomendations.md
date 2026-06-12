---
title: "Dual Boot (again) and Reccomendations"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by alexyip on 2007-01-04
Hi all, Newbie onboard.

I did use Linux and use dual boot but it was a long time ago. Tried to search the forum but too much results.

Can anyone tell me how to create dual boot Ubuntu and XP? or just show me link of the tutorials.

How to select operating system when boot?

What is an ideal partition for dual boot on my laptop that installed 40GB harddisk?
10GB Linux, 30GB XP?

That's all for now, will post more Q later, gotta take some sleep. It's 3AM here.

---

### Post by energiya on 2007-01-04
The main ideea is that you have to create at least 2 paritions for linux. One has to be the SWAP partition, and the other(s) used to store data. It is recomanded that your swap partition has at least the amount of RAM memory (but if you have a lot of memory, swap will be mostly empty), and at least 2.5 GB for installing files. For example, I have 1.2 GB for /home , 4.8 for the rest and 300MB for swap (128 MB RAM), 4GB for win and the rest (almost 30GB) shared.
As for selecting wich OS to boot, Ubuntu installs the GRUB boot-loader on the MBR (recomanded), and when starting up, a nice menu appears in wich you can choose your OS.

---

### Post by mykalreborn on 2007-01-04
you could do what i did. i also have a 40 gb hdd.
first format the whole hard-drive. do not format in any file system just live it blank. you can do that with the windows installer or with gparted:[link]("http://gparted.sourceforge.net/livecd.php"). 
then install win xp because it's much easier. install it on a 10 gb  fat32 partition so you won't have any trouble with any ntfs non-sence. then install ubuntu on a 10 gb ext3 partition and don't mount /home on the remaining 20gb as you want to keep those bytes for sharing between OS's. keep /home on the root partition and mount the remining 20gb in something like /mnt/shared or /mnt/whatever. format it in fat32 and your set to go ;)

---

