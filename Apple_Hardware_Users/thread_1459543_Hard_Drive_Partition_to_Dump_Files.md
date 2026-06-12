---
title: "Hard Drive Partition to Dump Files?"
date: 2010-04-21
forum: Apple Hardware Users
---

### Post by Cygni on 2010-04-21
Hi!

Wondering if it is possible to create a small 1-5 GB HD partition to dump files, so I can access them from Ubuntu or Leopard? If possible, would I used Boot Camp, Ubuntu, or some other partitioning device? 

Thanks!

Details:
MacBook
Leopard OS and Ubuntu Beta 2 (Installed using BootCamp and ReFit)
FileVault on

---

### Post by dannyboy79 on 2010-04-21
you could create a fat32 partition and access it from either ubuntu or OSX. good luck, you could use boot camp again to resize your ubuntu partition to make it a little smaller to then create your fat32 partition. why not use cloud storage if it's only 1.5 GB. Dropbox or even UbuntuOne are free cloud storage services.

---

### Post by Cygni on 2010-04-21
Thanks!
I just tried BootCamp, but it is only allowing a restoration to the original drive space. 
Think working from the Ubuntu partition will be easier.

The online storage, like Ubuntu's and MSN, are limited in methods of uploading. Meaning, I can only upload files - if I could upload folders or transfer a bunch of files by allowing access to my drive (my professional online drive space allows this), I would. 

Will update after I attempt partitioning from Ubuntu. :)

---

### Post by dannyboy79 on 2010-04-21
hold up, dropbox basically sync's a folder on your desktop to it's server for free. up to 2gb for free. i thought ubuntuone did the same. you would just put the files there that you want to be able to access from either ubuntu or OSX and those files would show up in OSX in whatever folder you told it to sync to as well as the folder you told it to sync to in ubuntu. what is the partition that you want to shrink? is it HFS or merely ext3 or ext4. if its the later, then yes, you could jsut do this from an ubuntu livecd using gparted. good luck

---

### Post by Cygni on 2010-04-21
> **dannyboy79 said:**
> hold up, dropbox basically sync's a folder on your desktop to it's server for free. up to 2gb for free. i thought ubuntuone did the same. you would just put the files there that you want to be able to access from either ubuntu or OSX and those files would show up in OSX in whatever folder you told it to sync to as well as the folder you told it to sync to in ubuntu. The files I want are on the OS X partition, if I am unable to get this to work, will check and see if I can sync the Mac OS on Ubuntu One.


> 
 what is the partition that you want to shrink? is it HFS or merely ext3 or ext4. if its the later, then yes, you could jsut do this from an ubuntu livecd using gparted. good luck
I am logged into Ubuntu now and it is ext4. I'll fin the CD and give it a try  in a few.
Thanks, again!

---

### Post by dannyboy79 on 2010-04-21
[QUOTE=Cygni;9155175]The files I want are on the OS X partition, if I am unable to get this to work, will check and see if I can sync the Mac OS on Ubuntu One.[QUOTE]
dropbox is compatible with mac osx.

---

### Post by srs5694 on 2010-04-21
GNU Parted (text-mode; command name parted) or GParted (GUI; command name gparted) should be able to resize Linux partitions, and I believe HFS+ partitions if the appropriate HFS+ support packages are installed. OS X's Disk Utility can also resize HFS+ partitions, at least on recent versions of OS X on Intel-based Macs. (I'm not sure if it can do the job on PPC-based Macs.) With partitions resized, you can then create a new partition for file sharing. FAT should work fine for small files, or you can use unjournaled HFS+ for more flexibility; however, you should have a better understanding of Unix permissions if you use HFS+, since your Ubuntu and OS X UIDs are unlikely to match.

One caveat: If you're using an Intel-based Mac and rely on a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) configuration for anything, mucking with your partition table by resizing partitions is potentially disruptive. You should understand what you're doing, and know what your partition tables (both MBR and GPT) look like before proceeding. Use fdisk (in Linux or OS X) to view the MBR side, and gpt (in OS X) or gdisk (in Linux) to view the GPT side.

---

### Post by Cygni on 2010-04-21
> **dannyboy79 said:**
> [QUOTE=Cygni;9155175]The files I want are on the OS X partition, if I am unable to get this to work, will check and see if I can sync the Mac OS on Ubuntu One.[QUOTE]
dropbox is compatible with mac osx.
Will look into it Dropbix tonight, thank you.

---

### Post by Cygni on 2010-04-21
> **srs5694 said:**
> GNU Parted (text-mode; command name parted) or GParted (GUI; command name gparted) should be able to resize Linux partitions, and I believe HFS+ partitions if the appropriate HFS+ support packages are installed. OS X's Disk Utility can also resize HFS+ partitions, at least on recent versions of OS X on Intel-based Macs. (I'm not sure if it can do the job on PPC-based Macs.) With partitions resized, you can then create a new partition for file sharing. FAT should work fine for small files, or you can use unjournaled HFS+ for more flexibility; however, you should have a better understanding of Unix permissions if you use HFS+, since your Ubuntu and OS X UIDs are unlikely to match.

One caveat: If you're using an Intel-based Mac and rely on a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) configuration for anything, mucking with your partition table by resizing partitions is potentially disruptive. You should understand what you're doing, and know what your partition tables (both MBR and GPT) look like before proceeding. Use fdisk (in Linux or OS X) to view the MBR side, and gpt (in OS X) or gdisk (in Linux) to view the GPT side.
I have already partitioned the Ubuntu partition using GParted. Just need to figure out a way to access from Leopard.

Everything is backed up, so not too concerned about having to start over.

---

### Post by jbiggs12 on 2010-04-22
So you've resized your Ubuntu partition to make way for a shared partition, and you've created a new partition that should hopefully be read by Ubuntu, correct? Just format the partition as FAT32, and you should be on your way. 

Dropbox would also work; however it can be kind of a pain to wait on large files to download, especially when you've been on one partition for a while and can't choose download priority of all of the files you've created. Plus it won't be very nice with you if you shut down without letting Dropbox upload everything, you'll have to go over to the other partition and then switch back. Dropbox will work, and it's a nice service, but it is not for the impatient. Just my $.02.

Cheers, Jack

---

### Post by dannyboy79 on 2010-04-22
he only wants about 1.5 gb if i read the original thread correctly. so downloading files isn't really an issue except for maybe the first time, dropbox auto syncs a selected folder on your desktop with it's online server. so you change a file on your computer in ubuntu, then it auto syncs up to the dropbox seerver. you open Apple OSX, the file will start to sync up with the folder you selected in OSX before ya know it.

---

### Post by Cygni on 2010-04-23
> **jbiggs12 said:**
> So you've resized your Ubuntu partition to make way for a shared partition, and you've created a new partition that should hopefully be read by Ubuntu, correct? Just format the partition as FAT32, and you should be on your way. 

Dropbox would also work; however it can be kind of a pain to wait on large files to download, especially when you've been on one partition for a while and can't choose download priority of all of the files you've created. Plus it won't be very nice with you if you shut down without letting Dropbox upload everything, you'll have to go over to the other partition and then switch back. Dropbox will work, and it's a nice service, but it is not for the impatient. Just my $.02.

Cheers, Jack
Dropbox is OK, but slow and small... there's a joke in there somewhere. :p
Anyway, I completed everything this morning and will definitely new HD space when on the MacBook and use Ubuntu storage over Dropbox because it does not require downloads. Love that! As I move between computers quite a bit. 


> **dannyboy79 said:**
> he only wants about 1.5 gb if i read the original thread correctly. so downloading files isn't really an issue except for maybe the first time, dropbox auto syncs a selected folder on your desktop with it's online server. so you change a file on your computer in ubuntu, then it auto syncs up to the dropbox seerver. you open Apple OSX, the file will start to sync up with the folder you selected in OSX before ya know it.
*She* ended up creating a 5gb partition for transfer of larger folder and projects that require more space. The transfer is quite fast. :)

---

### Post by Cygni on 2010-04-23
After partitioning, I had to take a break from tinkering for work and other projects.
Came back to it today, verified the "free space" in OS X  DiskUtil. then rebooted into Ubuntu and verified the same. I used the Admin drive tool to format the "free space" to FAT and check that it shows in both OS. Which it does!

Tested a fairly large file of primary source material and bingo! Available for transfer!
Thanks to all for your assistance, I greatly appreciate it! :)
[COLOR=Gray]
For anyone wondering, I used thread tool to mark this thread as solved. The info was not an easy find.[/COLOR]

---

### Post by dannyboy79 on 2010-04-23
Disregard

---

