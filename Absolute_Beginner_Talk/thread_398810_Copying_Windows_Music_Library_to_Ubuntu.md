---
title: "Copying Windows Music Library to Ubuntu"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by flubmasterq on 2007-04-01
I'm pretty new to Ubuntu and I'm trying to figure out how to copy my music library from Windows to Ubuntu.
Is this possible?

'Cause I have a HUGE music library and I don't want it to go to waste because I transfered to Ubuntu.

Thanks in advance,
flubmasterq

---

### Post by spin2cool on 2007-04-01
You're going to have to be more specific.

Where is the music now?  On your windows partition?  If it's NTFS, you canmount it read only and listen to your music just fine.  You can create a shared FAT32 parition and move all the music there, so you can read/write from both windows and linux.  You can do the same with a ext3 parition and Ext2 IFS for windows.  You're going to have to be more specific if you wnat reasonable help.

---

### Post by irish_flu on 2007-04-01
Sure you can.

A couple of questions:

Are these files mp3 files?

Are you wanting to move/copy the music into the Ubuntu partition, or do you just want to access the (Windows) drive where it's already stored?

Is this storage on the same computer (in a different hard drive partition) or is it on another computer (hopefully one you can access from your Ubuntu box over the network)?

---

### Post by flubmasterq on 2007-04-01
Sorry I wasn't specific enough, I was in a hurry when I wrote it.

Most of them are mp3's, some are wma's though, but I can convert them easily.

Right now I just want to access them from the Windows drive, but later on I might want to copy it to the Ubuntu drive.

It's all on the same computer, but I'm currently running Ubuntu on a disc until I can figure out how to get my Windows music onto here.

---

### Post by zvacet on 2007-04-01
Do you have an icon hd1 or something similsr in you upper left on desktop.if you have it is your windows partition.You can access it by click on it .after that just copy/paste(that is the way i use to do).Another solution is to make fat32 partition in case you want to have access from windows and from Ubuntu.In that case fat32 will be shared partition in wich OS can read and write.

---

### Post by SorenK on 2007-04-01
I just moved my music to my ext3 partition yesterday.

To get mp3 files playing in Ubuntu, there are some packages you need to install.  Details here:

[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

Here's something you need to figure out.  Can you install the needed packages for mp3 files using the live cd?  Will it stick around if you restart the computer?

I booted off the live cd a couple of times, but then I installed to some empty space on my hard drive, dual booting with XP.  So I don't know if you can install packages for the live cd and have them stick around after a reboot.

Since you want to access them from Windows, keep them on an NTFS drive.  Get them all organized as you like in a folder and mp3s for the WMAs made.  Then drag it into Rythmbox.  Alternatively you can use Rythmbox's library set up function. Ctrl-O or File-->Import Folder.

Rythmbox is found in Applications --> Sound & Video

---

### Post by flubmasterq on 2007-04-01
The problem is, I don't know how to access an NTFS folder.

---

### Post by spin2cool on 2007-04-01
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

slightly farther down, you'll see how to install NTFS read/write support, but use that at your own risk - I've heard conflicting reports.

---

