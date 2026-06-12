---
title: "Drive letters"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by neelabhro on 2006-07-16
I'm trying to get linux off my dual-boot pc. However one thing has led to another and I need to get the Linux partition to show up with a drive letter, since my XP Partition Magic can't read it. Is there any way to get around this/get a drive letter simulated in Linux??

---

### Post by coffeecat on 2006-07-16
> **neelabhro said:**
> Is there any way to get around this/get a drive letter simulated in Linux??


Not that I know of. But if you're simply trying to delete your Linux partition, boot up with the Ubuntu Dapper live CD, and use Gparted (System > Administration > Gnome Partition Editor) and delete it there. Then Partition Magic should see the space as unallocated or unformatted and you can do what you want with it.

Or you can use Gparted to reformat your Linux partition into either ntfs or fat32 - of course you'll lose all the data on the partition - and then Windows should allocate a drive letter, or you can do that somewhere in the Windows Control Panel.

---

### Post by Sef on 2006-07-16
Partion Magic does not like linux.  Better to download and use [GParted.]("http://gparted.sourceforge.net/livecd.php") That should take care of your problem.

---

### Post by coffeecat on 2006-07-16
Another thought, neelabhro. If you don't mind spending a little money and you are going to be using both Windows and Linux for some time yet, have a look at Acronis Disk Director. It's a Windows program but it can recognise, delete and create Linux partitions quite happily. And it will label partitions which, to my mind, is one big omission in Gparted. I find that the two complement each other nicely, and I use both. When I bought my copy it was bundled as a special offer with Acronis True Image - a disk imaging and cloning app. That's very good too.

---

### Post by Stew2 on 2006-07-16
I recently aborted a Dapper install and ended up with a blank 20 gig partition on my hard drive. I did like Coffeecat said and used gparted on the Dapper live CD to delete the partition I didn't want, I then used gparted again to resize my existing Windows partition to use the whole disk again. Gparted worked great! :D

---

