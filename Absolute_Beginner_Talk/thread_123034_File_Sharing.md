---
title: "File Sharing"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by blud on 2006-01-29
My Computer has several harddrives in it all of which have been used with windows for quite a while and have many files on them that I would like to make available to me whilst I am using Ubuntu I have read in several places that while your in Windows it is not possible to access your Linux partitions however I don't ever recall reading anything about the other way around. So can anyone help with transfering my windows files to Linux or is it not possible.

---

### Post by Fffan on 2006-01-29
I'd be quite intereted in this as well, as i have several CDs in .wav that i dont feel like doubling up in a seperate partition, as the linux partition is only 6gigs freespace until my new 200gig comes in, so help is appreciated!

---

### Post by Madpilot on 2006-01-29
[https://wiki.ubuntu.com/AutomaticallyMountPartitions](https://wiki.ubuntu.com/AutomaticallyMountPartitions) should help.

Note than Linux can read but not (safely) write to XP's standard NTFS partitions; both Linux & Windows can read & write safely to FAT32, though.

Apparently you can get an application to read Linux's ext3 partitions in XP, too.

---

### Post by DoorGunner on 2006-01-29
yes i agree with MadPilot..... A Fat32 share file is the way to go..... For the future it looks like the new 2.6.15 kernel will have the ability to read and write to NTFS. However, keep in mind this is new. I would be leary at this point using it.

---

### Post by blud on 2006-01-29
So would formating one of my harddrives to afat32 partition mean that I could easily transfer files between Linux and Windows is this correct if so can someone inform me how to format a complete harddrive to a fat32 partition

---

### Post by mstlyevil on 2006-01-29
[QUOTE=blud]So would formating one of my harddrives to afat32 partition mean that I could easily transfer files between Linux and Windows is this correct if so can someone inform me how to format a complete harddrive to a fat32 partition[/QUOTE]

First off if you are using Windows XP then you will want to create 3 partitions during a complete reformat of the drive. First you create the OS partition for XP. I would make it no less than 10 GB and Idea would be 20 GB. You will want that first partition to be NTSF. You will create the other two partitions during the reinstalation of XP. The size you make them will depend on how much storage space you will want in the second partition. The third one will be your Linux partition so the size of that will depend on how much space you want to allocate for that. Once XP is installed, go ahead and install your drivers and updates first. After that you will go to My Computer and look for the second logical hard drive. (It should be E if you only have one optical drive) Right click on it and follow the menu to Format. Click on that and in the menu change the file system to FAT 32. Then click format. After you are done with that just move My Documents to that drive. Then you go and install Ubuntu on the last partition as normal. 

Edit: As far as I know you are supposed to be able to transfer files. I have not tried it personally yet.

Now if you are using a seperate hard drive then  skip reinstalling Windows. Just install the drive and follow the steps starting with going into My computer. You can format the drive into FAT 32 right from Windows.

---

### Post by DoorGunner on 2006-01-29
I would just make another partion for things that you share....IE mp3's Pictures documents etc/

---

### Post by blud on 2006-01-30
I am trying to turn one of my 200 Gig hard drives into a fat32 partition so as I can share all my files between Linux and Windows. Am wondering if it is possible to format a complete drive with fat32 as the largest partition of fat32 I can create is 30 Gig 
Am doing this in Windows and not Ubuntu.
Is it possible to do in Linux maybe?

---

### Post by DoorGunner on 2006-01-30
I dont see why not.....

Just remember fat32 will not run files over 2GB in size. (programs most likely)

I use gparted in linux to create partitions and partition magic for windows. Both are fairly good

---

### Post by m.musashi on 2006-01-30
[QUOTE=blud]I am trying to turn one of my 200 Gig hard drives into a fat32 partition so as I can share all my files between Linux and Windows. Am wondering if it is possible to format a complete drive with fat32 as the largest partition of fat32 I can create is 30 Gig 
Am doing this in Windows and not Ubuntu.
Is it possible to do in Linux maybe?[/QUOTE]

If I'm not mistaken, you cannot format a fat32 partition larger than 32GB from XP (although you may be able to from somewhere else). If you have a 200GB drive you would most likely need to create several 32GB partitions. This page has some info that may clear things up.

[http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/windows/xp/all/reskit/en-us/prkc_fil_cycz.asp](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/windows/xp/all/reskit/en-us/prkc_fil_cycz.asp)

As other suggested, I'd only format enough space for the files you need to access in both environments. If that is more than 32GB you may run into problems.

---

