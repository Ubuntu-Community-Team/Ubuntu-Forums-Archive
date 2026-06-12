---
title: "Partitioning for XP/Ubuntu dual boot"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by LouIII on 2007-01-27
I currently have XP installed and want to install Ubuntu too so I can dual boot.  Please tell me if the following partition scheme will work.

I have a 120GB HDD, all of which is currently an NTSF partition that's my C drive.  I want to use Partition Magic to reduce C to 30GB, then create two extended partitions of 10GB each (10GB for XP OS, 10GB for my XP-only data, and 10GB for my wife's data).  Then I'll create a 60GB FAT32 primary partition for data that XP and Ubuntu can both use.  I'll leave the remaining 30GB unpartitioned and direct Ubuntu's install process to create a partition there and install into it.  Should this work?  

In case you're wondering, I won't use Partition Magic to install Ubuntu, nor will I use Boot Magic.  I'll install Ubuntu directly from the CD, and I'll let it set up GRUB.

---

### Post by riven0 on 2007-01-27
Sounds like a lot of partitions. I don't see why it won't work, but instead of having two 10GB partitions for the XP OS and then the XP data, why don't you just make it one 20GB partition?

Other than that, just make sure you defragment your hd when doing that many partitions. And do a backup, because Partition Magic is known to cause errors sometimes.

---

### Post by LouIII on 2007-01-27
Thanks for your reply.  I'm just in the habit of having a separate drive for my music, games, and other non-system data.  I also wanted a separate drive for my wife, because I don't want her fumbling through the sytem files or my stuff.  But I guess I could leave the 30GB for XP as one drive, and my wife and I could use our My Documents folders instead of having separate drives.

My main concern was that the 60GB shared OS FAT32 partition would be accessible by both OS's.

---

### Post by jammodotnet on 2007-01-27
I did mine in a similar fashion:
120GB drive in 4 partitions:
* XP (ntfs) @ 30G
* Ubundu (ext3) @ 45G - swap @ 2G
* SHARE (fat32) @ 45G

the share is the one that is commonly shared by both OSes, has 3 main directories:
win specific downloads/files
linux specific downloads/files
unspecific downloads/files (MS Office documents, OO documents, Forefox bookmark backups)

This is my first time every doing a successful dual-boot with XP Pro and Ubunu 6.10. :)


EDIT: oh yeah, the reason i made the XP so much smaller than the linux is cause over the years, ive added and removed and added and removed and finally settled on the 'Necessary Apps' needed with every XP re-install. So by now, I know all my much needed apps installed are minimal -vs- Ubuntu ... i just dunno man! :)

---

### Post by LouIII on 2007-01-27
That seems to be the best way.  Partition Magic recommends setting up the 60GB shared OS drive as a logical drive.  Does it matter whether it's primary or logical?

---

### Post by jammodotnet on 2007-01-27
> **LouIII said:**
> That seems to be the best way.  Partition Magic recommends setting up the 60GB shared OS drive as a logical drive.  Does it matter whether it's primary or logical?

uh oh, i dont remember which is primary -vs- logical.
i *think my XP partition is my primary*, but i could be wrong, it was a trial and error sort of thing for me.

but i wanted to remind you to do a THOROUGH defragmentation on your Windows first BEFORE you install ubuntu. it made my re-installation a breeezze.
i used: [http://www.majorgeeks.com/O&O_Defrag_2000_Freeware_Edition_d4545.html](http://www.majorgeeks.com/O&O_Defrag_2000_Freeware_Edition_d4545.html)

it was pretty cool, cause ive been using it for some time and recommending it to friends.
before I did mine for the final installation, i used the default Windows defrag utility, and then followed up by this one, and it was amazing how much better than Windows it was.

---

### Post by tryll1980 on 2007-01-27
not really. I run dual XP/Ubuntu too....and the ubuntu partition is logical....but just remember to backup important data before doing any partition work:)

---

### Post by housam on 2007-01-27
You only able to create 4 primary partitions on a single HDD. If you need more partitions , you have to convert one of the primary partitions to an extended partition which can be devided to any number of partitions you want.
Please note that partition magic is not the suitable tool for partitioning for ubuntu. use the Gparted to do the job, it is perfect for ntfs and ext3 format.
Do the defrag at least twice before resizing your xp partition and create all your partitions manually before installing ubuntu, that put every thing under control.

---

### Post by LouIII on 2007-01-27
Thanks, everybody.  My plan was to use Partition Magic to set up the NTSF XP drive and the FAT32 shared OS drive, then let Ubuntu's install process partition and format the remaining free space.  Alternately, I guess I could use Gparted to do the Ubuntu partition and the shared OS partition.  Would it matter in terms of the shared OS partition?  The XP partition is already done.

---

### Post by LouIII on 2007-01-27
I set up my XP and Shared OS partitions with Partition Magic, then told Ubuntu to install into the remaining free space.  It worked perfectly, and I'm in Ubuntu as I write this post.  Thanks again for your help.

---

### Post by housam on 2007-01-28
Congratulations. Glad to here you did it.

---

### Post by Maestro23 on 2007-01-28
> **LouIII said:**
> I set up my XP and Shared OS partitions with Partition Magic, then told Ubuntu to install into the remaining free space.  It worked perfectly, and I'm in Ubuntu as I write this post.  Thanks again for your help.

New user here as well.  This is how I set up my dual boot too.  Everything is running very smoothly.  I'm running XP and Xubuntu.  Loving Xubuntu.:D

---

### Post by geoth on 2007-01-28
I have a single 160 gig master hard drive.
My current xp/ubuntu dual boot set up is :
50gig xp (ntfs)
80-ish gig Ubuntu w/ 2.5 gig swap.

---

