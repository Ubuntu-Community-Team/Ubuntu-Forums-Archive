---
title: "is it not safe to write to NTFS?"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by Thundercat on 2006-06-23
Just looking through the desktop guide and came across the "mounting windows partitions" bit.
It says: "If your Windows partition uses the FAT32 filesystem, it is safe to allow read-write access to the partition. "

So can someone explain why it is unsafe to write to NTFS? Is it impossible or merely unwise? 
My RAID array is where I store all my photos etc. and I'd like to be able to access it RW through Linux as well as Windows and it is formatted as NTFS. 

Thanks :)

---

### Post by Brunellus on 2006-06-23
it's possible.  not very wise, unless you enjoy irrecoverable filesystem corruption.

You have been warned.

---

### Post by yager on 2006-06-23
Go to this link at your own peril.

Those meek of heart, turn back now.

[https://wiki.ubuntu.com/Lkraider/NtfsFuse?highlight=%28ntfs%29%7C%28%2Bfuse%29](https://wiki.ubuntu.com/Lkraider/NtfsFuse?highlight=%28ntfs%29%7C%28%2Bfuse%29)

---

### Post by Anduu on 2006-06-23
I have been using ntfs-fuse for quite a while now and have suffered no ill effects.

---

### Post by Kilz on 2006-06-23
[QUOTE=Anduu]I have been using ntfs-fuse for quite a while now and have suffered no ill effects.[/QUOTE]
But writing to ntfs is still experimental, you take a chance of corrupting the entire drive. Better to create a small fat32 partition to store files you want to transfer between Linux and windows. That way is safe.

---

### Post by catlett on 2006-06-23
[QUOTE=Kilz]But writing to ntfs is still experimental, you take a chance of corrupting the entire drive. Better to create a small fat32 partition to store files you want to transfer between Linux and windows. That way is safe.[/QUOTE]
Just to reiterate. Make a fat32 partition for data on your drive. Put your photos, documents etc on there. Leave the XP "system" on ntfs and the Ubuntu "system" on Ext3 but put your data on fat32. This way your systems will run at optimal speed and efficiency, by being on the filesystem created for them,  and you will be able to safely access your data from either one. This is also a good practice in general (not just for dual booting purposes). If either system goes down your data is not lost. You can reinstall without worrying about loosing data during reformat.

Just another little tidbit if you want to keep it ext3 and ntfs. This is a driver for windows. It will allow you to read/write to ext2 and 3 a.k.a. ubuntu from windows. [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Kouya on 2006-06-24
yupz noobie here and i did FAT32 partition to act as a go between. All my stuff is in NTFS since well xp was the only OS i ever used and i'm too lazy to backup my NTFS drives as I have gigabytes of stuff there...

so far ubuntu pwns...i basically do almost everythg in it...

---

### Post by Thundercat on 2006-06-26
My situation is this: I have a 1Tb RAID array already configured and full of data, formatted as NTFS under windows XP.
I'd like to be able to read/write to this when I'm in ubuntu... would the following solution work? 

Run a Windows XP VMWare machine under Ubuntu and have that machine access the RAID array and share it on the network, then ubuntu can effectively access the drive as a network share.

(Someone is bound to ask, so the reason I have and need access to the 1Tb drive is that I'm a photographer. The drive is mostly full of my images.)

---

### Post by steve.horsley on 2006-06-26
The reason that writing to ntfs is still experimental is that MS will not publish the filesystem specification so all ntfs access must be reverse-engineered. Obviously, figuring out how to read files is a lot safer than trying to write them when you're not sure how the file system works. Given this and the fact that you have a lot of important data, I really don't think you want to try writing to it from Linux.

I don't know if windows can read real raid arrays from inside VMware. If it can then you should be OK. It's really a question of how transparent the VMware hardware access is.

---

### Post by mozetti on 2006-06-26
Just to chime in -- I corrupted a NTFS file system writing to it from linux. I don't think it was the ntfs-fuse mentioned here, but it was another respectable ntfs-writing tool. If you don't want to lose the partition, then don't write to it from Linux.

---

### Post by Thundercat on 2006-06-26
Like a lot of you have said I DON'T want to risk corrupting all that data so I won't be mounting the RAID array in Linux. 
If we assume the RAID array will work like a normal drive to the VMware image, has anyone got experience of running an XP VMware image and accessing other drives from it? 
I'll be running Ubuntu on a 30Gb IDE drive, will have a 500GB SATA drive with winxp to dual boot to for games and the Raid array with data on.

---

### Post by catlett on 2006-06-26
You will be able to read and therefore access your photos from ubuntu. The issue is when you have new data while in Ubuntu and you want to write that info to XP's partition. Here is a workaround that won't have any risks although it will add astep in your data saving process.
[http://www.fs-driver.org/](http://www.fs-driver.org/)  That is a link to an ext2 driver for windows. With that driver you can access your Ubuntu partition from windows. So when you are in ubuntu and you have new data you want to use in XP as well. Save it in your Ubuntu home folder. Boot into windows. Access the folder through explorer like you would any other folder. Then copy the data over to "My Pictures" or any other windows folder. It adds a step but you won't be risking corruption.

---

### Post by Breezy Badger on 2006-06-28
Is there any way to format a large drive, say 150 GB or more, in a format that both systems can use, like FAT32.

---

### Post by matrooswolf on 2006-06-28
What about this?
[http://wiki.linux-ntfs.org/doku.php?...he_ntfs_driver](http://wiki.linux-ntfs.org/doku.php?...he_ntfs_driver)

It says here that there are no problems writing to Ntfs (see section 3.2)

> The next huge step towards much improved write functionality was the release of ntfsmount as part of ntfsprogs, in 2005. Ntfsmount has almost full feature write support. It can resize, create and delete files and directories and even operate on symlinks, devices, FIFOs and sockets. Though ntfsmount has still some restrictions, **data safety should not be in risk**, especially if you make regular backups with ntfsclone. This is a highly adviced, given that the most often problems we are reported are physical hard disk failures!

So what about it?  Does somebody have any experience with this? Just wondering...

(No I haven't, and I am not going to ;))

---

### Post by aysiu on 2006-06-28
[QUOTE=Breezy Badger]Is there any way to format a large drive, say 150 GB or more, in a format that both systems can use, like FAT32.[/QUOTE]
Yes. Any Linux partitioning program can do this (GParted, QTParted, DiskDrake). Windows will not make a FAT32 partition that large, though.

---

