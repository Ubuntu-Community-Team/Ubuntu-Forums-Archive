---
title: "My Book external hard drive question"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by suki on 2006-12-25
I might be in the possession of a My Book 160 GB Essential Edition USB 2.0 external hard drive made by WD (Western Digital). 

Will I face problems with using this on Ubuntu? It says that it has a Google feature to locate and organize files for Windows only. Also known compatibility with the following: Windows 98SE/Me/2000/XP and Mac OS X 10.2.8+.

If you have any experience with My Book, please share with me. Also if this will not work out with Ubuntu please share suggestions to compatible external hard drives. 

SimpleTech's external hard drive pose any problems?

---

### Post by dbbolton on 2006-12-25
i've never heard of an external hard drive that wasn't "linux compatible," but then again i don't personally use one :/

---

### Post by louieb on 2006-12-25
> **suki said:**
> I might be in the possession of a My Book 160 GB Essential Edition USB 2.0 external hard drive made by WD (Western Digital). 
Got one for Christmas.  Works alright. Has a 160 gig fat32 partition. It does seem to be a little slow. I going to reformat it 50/50 between NTFS and ext3 and see if that speed it up any. The WD site says NTFS is faster than fat32.

---

### Post by mike3k on 2006-12-25
I have one connected to my Buffalo Linkstation (which is Linux-based) as a backup device, formatted as ext3. It works beautifully.

---

### Post by suki on 2006-12-25
> **louieb said:**
> Got one for Christmas.  Works alright. Has a 160 gig fat32 partition. It does seem to be a little slow. I going to reformat it 50/50 between NTFS and ext3 and see if that speed it up any. The WD site says NTFS is faster than fat32.

I am unfamiliar with ext3. What is this? Can data on a ext3 formatted drive be accessed by Windows XP?

---

### Post by logos34 on 2006-12-25
explore2fs

[http://sourceforge.net/search/?words=ext3fs&type_of_search=soft&words=explore2fs](http://sourceforge.net/search/?words=ext3fs&type_of_search=soft&words=explore2fs)

---

### Post by riven0 on 2006-12-25
> **suki said:**
> I am unfamiliar with ext3. What is this? Can data on a ext3 formatted drive be accessed by Windows XP?

ext3 is one of the most popular linux file systems. You're probably using it right now. :)

EDIT: Also, I'm not sure about xp accessing ext3. Someone else more knowledgeable will have to comment on this.

---

### Post by SushantAmin on 2007-11-12
Hi everyone,
I purchased a Western Digital My Book Essential 500 GB, and have found a strange issue regarding its partitioning.

I used cfdisk to repartition it, which worked fine (1 FAT, 1 ext2), using  ubuntu 6.06.

Now, WD has a partition that includes the software utilities, plus the  google installers. This partition never disappears, rather, is mounted every time. Also, mount displays its size as the complete size of the disk. My ext2 partition automounts fine, displaying its half of the disk.

I think WD added a workaround somewhere in the drive electronics to virtually display this partition and its related data, instead of actually writing it to disk. I am not able to delete/change type/resize this partition. 

WD forums do not support any other OSs than Windows & the Mac.

Do let me know your comments on this.
Cheers,
Sushant.

---

### Post by kathryn on 2007-12-24
I've just received a 500GB My Book.  Dead keen to give it a go.  I've been trying to access the WDC "knowledge base" (support.wdc.com) for information on using the drive with  two operating systems (namely XP and Ubuntu Gutsy, in my case).

I can't even get the website to load... irritating!



> **SushantAmin said:**
> Hi everyone,
I purchased a Western Digital My Book Essential 500 GB, and have found a strange issue regarding its partitioning.

I used cfdisk to repartition it, which worked fine (1 FAT, 1 ext2), using  ubuntu 6.06.

Now, WD has a partition that includes the software utilities, plus the  google installers. This partition never disappears, rather, is mounted every time. Also, mount displays its size as the complete size of the disk. My ext2 partition automounts fine, displaying its half of the disk.

I think WD added a workaround somewhere in the drive electronics to virtually display this partition and its related data, instead of actually writing it to disk. I am not able to delete/change type/resize this partition. 

WD forums do not support any other OSs than Windows & the Mac.

Do let me know your comments on this.
Cheers,
Sushant.

---

### Post by kathryn on 2007-12-26
Since my previous post I've started backing up data from Ubuntu and XP to the My Book Essential Edition (500 GB).  I had some initial problems but now things are working.  Note that I'm only using the drive as a data archive (no partitioning required).

Initially I left the file system as FAT32 (out of the box), and commenced copying files across.  After a seemingly arbitrary quantity of data had been transferred (e.g 6GB or 15GB), the data transfer would suddenly cease without an error in Ubuntu, but with an error in XP.  Apparently the drive was out of space (!) and I was encouraged to perform the beloved Windows "disk cleanup".  Clearly the drive was *not* out of space so I reformatted the drive to NTFS.

Ubuntu and XP are now happily copying data to My Book (and I can view the My Book's files from either OS).

Hope that helps. :)

---

### Post by AllanM on 2008-01-04
> **mike3k said:**
> I have one connected to my Buffalo Linkstation (which is Linux-based) as a backup device, formatted as ext3. It works beautifully.

Hi. Have just got a 750Gb MyBook essential for use with my linkstation pro. Sounds like you have something similar. My linkstation won't see it at all. Tried as xfs and ext3. Works fine connected to a laptop with UBuntu 7.10 but I really want to add it to the network. Any ideas? Thanks.

---

### Post by kathryn on 2008-01-06
Since my last post there have been a few developments regarding my experience with the Western Digital 500GB My Book (see quoted text below).  Hopefully this information will be helpful to future users of the device.

**To summarise the text below, I've had no problems using the 500GB My Book with Ubuntu (Gutsy), XP and Vista as a FAT32 data archive (backup drive).  That is, it worked straight out of the box for me.  (Hooray!)**

The longer story, for those interested:

Initially the reformat to NTFS seemed to suppress the "error copying file or folder" (lack of disk space) message, but the error reappeared.  The copying procedure would encounter a random file e.g. a small image and return the error.  No files (regardless of size) could be copied after that time.

The retailer kindly offered to replace the item without filing a customer warranty claim.

I took home a replacement 500GB My Book (fresh out of the box, **FAT32** file system).  I managed to copy across 60GB of data (from Vista and XP on different machines).  However while copying a folder of recorded video from my DV camcorder, the **same** error appeared as before.  As it turns out, the XP error message was the same but the underlying problem was different - I'd forgotten that FAT32 cannot store individual files exceeding 4GB, and the error-provoking file was 4.7GB.

The XP error message is frustratingly vague - copying a 4.7GB file to a FAT32 device produces the same message as a faulty device.  (Can you tell why I'm gradually using Ubuntu more than XP? :tongue: )

FAT32 is the ideal format for an external drive (at least for backing up data) due to its compatibility with Linux, Windows and Macintosh computers.  Since I have Linux and Windows machines at home, and some Mac computers at uni, I figure FAT32 is the best option for me.  

NTFS does indeed allow you to copy across files larger than 4GB, but you won't be able to use the device with all three types of operating system (only Linux and later versions of Windows, to my knowledge).  I've also read (in this very forum) that users may or may not have problems with NTFS devices when using Ubuntu.

Best wishes,
Kathryn :)



> **kathryn said:**
> Since my previous post I've started backing up data from Ubuntu and XP to the My Book Essential Edition (500 GB).  I had some initial problems but now things are working.  Note that I'm only using the drive as a data archive (no partitioning required).

Initially I left the file system as FAT32 (out of the box), and commenced copying files across.  After a seemingly arbitrary quantity of data had been transferred (e.g 6GB or 15GB), the data transfer would suddenly cease without an error in Ubuntu, but with an error in XP.  Apparently the drive was out of space (!) and I was encouraged to perform the beloved Windows "disk cleanup".  Clearly the drive was *not* out of space so I reformatted the drive to NTFS.

Ubuntu and XP are now happily copying data to My Book (and I can view the My Book's files from either OS).

Hope that helps. :)

---

### Post by avai on 2008-01-31
I recently purchased a SimpleTech 160GB External Hard Drive and am running Ubuntu 7.04.

I'm an absolute novice when it comes to computer stuff, (I am capable of activating the terminal and coping/pasting). I plug in the device into my laptop and there is no indication that my computer recognizes it - no icons of a drive.

Any suggestions?

---

### Post by AllanM on 2008-01-31
As a follow up the MyBook drive has now been sent back as faulty. The fancy auto-power might be the cause of my problem. A simple (cheap) usb drive connected to my (linux based) linkstation fine but the MyBook was invisible. I've now bought a Linkstation Pro Duo which is working fine with Ubuntu as a client running Samba.

*I recently purchased a SimpleTech 160GB External Hard Drive and am running Ubuntu 7.04.*

Try looking in the /media folder to see if it has been mounted. 7.10 seems a little better at recognising hot plug devices so an upgrade could be a way to go.

Good luck all.

Allan.

---

### Post by avai on 2008-02-06
I now have an icon available for the drive (which only appears when I boot the computer without the drive plugged in), however, when I click on it, the following message appears:

> Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

More Details:
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
missing codepage or other error
in some cases useful info is found in syslog - try
dmesg | tail or so

Meanwhile, the output for the dmesg | tail is:

> [ 94.252000] sdb: Write Protect is off
[ 94.252000] sdb: Mode Sense: 21 00 00 00
[ 94.252000] sdb: assuming drive cache: write through
[ 94.256000] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[ 94.256000] sdb: Write Protect is off
[ 94.256000] sdb: Mode Sense: 21 00 00 00
[ 94.256000] sdb: assuming drive cache: write through
[ 94.256000] sdb: sdb1
[ 94.880000] sd 2:0:0:0: Attached scsi disk sdb
[ 94.880000] sd 2:0:0:0: Attached scsi generic sg1 type 0

This was done with using the command **mkdir /media/smt** and by the entry of the following into /etc/fstab:
> 
/dev/sdb1     /media/smt    ext3     rw,auto,exec,user,uid=1000     0     0

Any suggestions?

---

### Post by malty on 2008-02-06
I do not use an external drive, what I have is.....

HD 1 = winxp = 160G

HD 2 = 3 partitions all about the same size = 500G total.

Partition 1 = NTFS

Partition  2 = NTFS

Partition 3 = Ubuntu Gutsy

Formatted from WINXP using Acronis DiscDirector.

I constantly use both partition 1 & 2 for file and backup storage from both WINXP & Ubuntu . Files of all sizes, shape and colour with both read and write access. I have never ever had a problem, even though I have resized and reformatted several times for various reasons, allways using Acronis.
        What I do, and this is only my setup, it may not be the correct way, but it works for me.... 
                                                     Places/computer/160G volume (WINXP)
                                                                  /150g volume (NTFS partition 1)
                                                                  /158G volume (NTFS Partition 2) 
This gives me 3 desktop icons, this also shows in the "Places" menu. I do this after every startup, it takes 20 seconds. 
Hope this was usefull
                                                               Malty

---

### Post by kentpend on 2008-02-06
It is possible to access ext3 from windows.
I think I got the driver from [http://www.fs-driver.org]("http://www.fs-driver.org/")

---

