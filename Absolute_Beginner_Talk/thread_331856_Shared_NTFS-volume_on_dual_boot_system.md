---
title: "Shared NTFS-volume on dual boot system?"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Hallvor on 2007-01-05
I`m running Ubuntu 6.06 on an AMD Athlon 2500+ XP. I have a dual boot system with Windows XP sp2 on the smallest partition on the primary hard drive (16 gb) and an old secondary hard drive (8 gb) on which I have installed Ubuntu (Dapper).

I enjoy filesharing and would like eMule and Ubuntu (running eMule through Wine since amule performed horribly with painfully slow and frequent server disconnects) to share the secondary partition (NTFS) of the primary drive with Windows XP. However, even though I can read from the drive, I can`t figure out how to write to it from file sharing programs (eMule and uTorrent). Is it possible to use the same NTFS partition as Windows XP (secondary partition of primary drive (100 gb)), or would it be better to reformat it as a Fat32 and use it flawlessly on both OS? And if I do, would the max volume size be limited to 32 gb?

---

### Post by jvc26 on 2007-01-05
You would need to reformat it as FAT32 - NTFS can be read by linux (it mounts in read-only mode and also can be read/write from linux, but the drivers that allow you to read/write are in beta at the minute and I'm not sure how reliable they are (they may be very reliable - I'd recommend taking a peek at some post about them on here - search would point you in the right direction). FAT32 however is properly supported by both and doesn't require the use of beta drivers and so offers you an easier option - presuming that this is your current layout:

Disc 1:
Primary Windows partition (NTFS)
The data partition you want to write to (NTFS)
Disc 2:
The Ubuntu partition

The simplest option I think is to reformat the data partition as FAT32, and then write to that as FAT32 and you can then drag stuff onto your ubuntu/windows partitions from there from within the respective operating system (using the data partition as a drive to share the info between the two OSs) Dont try using the same partition as windows that could cause all kinds of 'interesting' problems. A simple reformat of the data partition to FAT32 should solve the issues that you are having.
I'm not 100% sure on the maximum formatted size for a FAT32 partition I'm afraid.
Hope that helps,
Il

---

### Post by Hallvor on 2007-01-05
Thank you! Appreciate it.

---

### Post by CroEragon on 2007-01-05
In your place i wouldn't format my partition into FAT32. I Have SATA drive with two partitions with windows and Kubuntu on it. I also have second IDE hard drive with two storage partitions. All partitions are NTFS (except Kubuntu one that is ext3) and i use beta drivers that Illuvator mentioned. I didn't have any problem with that beta drivers whatsoever. It works perfectly and doesn't cause any problem to me. In your place i would first try using beta drivers (called ntfs-3g) and if they make problems you always can reformat to FAT32. But i must warn you that FAT32 gets fragmented easily.
If you can't use drivers than format, but first try drivers. in my experience they are VERY stable.
You can find guide [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access").

---

### Post by bodhi.zazen on 2007-01-05
for read-write access to ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?&t=217009)

It seems reasonable stable in that I have not heard many, err any complaints ...

---

### Post by Hallvor on 2007-01-05
This is from your link, bodhi.zazen: 

[I]"WHAT YOU COULDN'T DO : 

The present limitations of this driver are 
- access to encrypted files
- writing compressed files (reading is ok)
- change file ownership and access right"[/I]

Does this mean that I can`t write rar or zip-files to the NTFS-drive?

---

### Post by bodhi.zazen on 2007-01-05
> Does this mean that I can`t write rar or zip-files to the NTFS-drive?

Good question, I am not sure ...

I think what it means is you can not write to a file that was compressed on the ntfs partition (windows has a compression algorithm). 

My guess it that you can write rar and zip files to the ntfs partition.

One caution , if you write a file, especially one you have downloaded, from linux to windows be sure to scan it for viruses (from windows).

---

### Post by CroEragon on 2007-01-05
I think it means that you cant access drives that are compressed. If you right click drive in XP you have option in properties that allows you to  compress whole drive (not with zip or rar, in transparent way) so it takes less space.
But i have at least one ntfs drive that is compressed in that way and i can write on all my ntfs drives (3 of them).
Keep in time that thread was posted July 17th, 2006 so they probably changed thing or two.
EDIT:i didn't notice your post bodhi.zazen untill after posting

---

### Post by bodhi.zazen on 2007-01-05
LOL CroEragon

You post complements mine nicely (I am afraid I am rusty on my windows skills :( )

---

### Post by jvc26 on 2007-01-05
@ CroEragon: Yup you're right there - its the drive compression thing which allows you to make your drive take up less space, not file compressions like .rar .zip etc :)
Il

---

### Post by krajni on 2007-01-05
i dont know much about ubuntu but i can tell u that once u cross the 60-65 gb mark fat 32 partitions become unstable in windows and are prone to crashing/corruption....i work in a repair shop and see this happen often....usually in a .9x(98 ME etc) kernel box but sometimes nt (2000 xp) kernel machines as well

---

### Post by Hallvor on 2007-01-05
Hello!

Just wanted you to know that I followed the instructions from this thread [http://ubuntuforums.org/showthread.php?&t=217009](http://ubuntuforums.org/showthread.php?&t=217009) (thanks to bodhi.zasen), and after installation and reboot the drive showed on my desktop! I can now drag and drop files between the drives, and file sharing applications can save files directly on the shared drive.

A big thank you to all! :)

---

