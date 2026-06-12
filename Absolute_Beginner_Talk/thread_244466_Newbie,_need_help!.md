---
title: "Newbie, need help!"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by netnut on 2006-08-26
Hi all,

I am completely new to Linux, but understand PC's pretty well from the Windows point of view..! I managed to install Edubuntu, after my ShipIt request finally arrived, but have given it way too much space for my liking (around 13.5 GB inclusive of the swap partition). Now, what I want is to reclaim some of those so that it is shared with Windows and Edubuntu. That's not the main problem that I am facing, though. I can't access my logical drives from Edubuntu, how can I do that? I tried modifying the /etc/fstab file... doesn't work, and the fact that I cannot connect my ADSL connection from Edubuntu doesn't help. 

So, specifically, I'd appreciate if anyone would help me in:
1. Making the logical drives on my hard drive accessible
2. Configuring my ADSL connection in Edubuntu
3. Reclaiming some of the hard drive space from Edubuntu.

The last one though, isn't my immidiate concern. Also, a slight query - why can't I play mp3 files?

Here is my hard drive map: (total around 80 GB)

C drive (hda1): FAT32 has WinXP on it (20 GB)
D drive (hda5): NTFS doesn't have much on it. I resized this partition to make way for Edubuntu. Has been reduced to 6.5 GB.
E drive (hda6): FAT32 has all my data (20GB)
F drive (hda7): FAT32 has some more of my data (20GB)

hda8 (13GB) is the Edubuntu "main partition" and hda9 (900MB) is the swap.

Thanks in advance!
netnut.

---

### Post by meng on 2006-08-26
Post your /etc/fstab please.
Regarding mp3 look here:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
The reason it doesn't work out of the box is legal/licensing-related, which I'm not an expert on.

---

### Post by kaamos on 2006-08-26
Hello!

For windows drives: [http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)
For mp3: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by netnut on 2006-08-27
I tried the tips given at page given by kaamos regarding windows drives. It doesn't work out. Here is the contents of the file:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda9       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,auto    0       0
/dev/hda5	/media/windows	ntfs	nls=utf8, umask=0222 0	0
/dev/hda6	/media/windows	vfat	iocharset=utf8,umask=000	0	0
/dev/hda7	/media/windows	vfat	iocharset=utf8,umask=000	0	0
/dev/hda1	/media/windows	vfat	iocharset=utf8,umask=000	0	0

I can only access the hda1 partition... all else give a mount failure error. Please help.

Regards,
netnut.

---

### Post by bodhi.zazen on 2006-08-27
Each device must have a unique mount point.

You have multiple /dev/hdax all mounted on /media/windows. this is like naming each partition C:\ rathere then c,e,f,g ....

The last being /dev/hda1

Try:
/dev/hda5 /media/hda5 ntfs nls=utf8, umask=0222 0 0
/dev/hda6 /media/hda6 vfat iocharset=utf8,umask=000 0 0
/dev/hda7 /media/hda7 vfat iocharset=utf8,umask=000 0 0
/dev/hda1 /media/hda1 vfat iocharset=utf8,umask=000 0 0

Use what names you will.
make sure mount pint exists;

sudo mkdir /media/hda1 /media/hda5 ......

---

### Post by Lord_Butler on 2006-08-27
I have a question that is kind of related. I just installed Ubuntu on my computer and I can't access my harddrives at all due to a mount failure error. If I go into "Computer" and click on one of my harddrives, it says this:

"error: device /dev/hdb1 is not removable

error: could not execute pmount"

Here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Any help? Thanks in advance guys!

---

### Post by infoseeker on 2006-08-27
Please list all your drives and partitions, with ```
sudo fdisk -l
```
PS. 'l' = small 'L'.
I see your 'hdb1' is not on the fstab list.

---

### Post by meng on 2006-08-27
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by netnut on 2006-08-28
Ok... thanks you guys... I can now access my local drives, but still there is some problem with the NTFS partition. It cannot be mounted. 
Now, where do I look for instructions to configure my ADSL connection? I tried pppoeconf, it gives some error messages "could not open.." and exits.

Regards,
netnut.

---

### Post by meng on 2006-08-28
At least you're making progress. I don't know the answer to either of the remaining issues (NTFS and ADSL), but I suggest you start a new thread with a more descriptive title. That way, it will catch the eye of someone who does know the answer. Everyone here needs help, you know!

---

### Post by Jareth on 2006-08-28
Hi nutnet,
what is your adsl modem, if its speedtouch 330 like mine, I've just finished getting mine to work through the usb.

There are a few guides for getting these to work, in the end i used this one:
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

If its any use or I can give you any help, just ask. I am a complete newbie too, so not sure how much help I can be. Just follow those instructions there and it should get going eventualy.

Of course you might not be using a speedtouch, so ignore everything I've just said.

Good luck!

---

### Post by bodhi.zazen on 2006-08-28
> **netnut said:**
> Ok... thanks you guys... I can now access my local drives, but still there is some problem with the NTFS partition. It cannot be mounted. 
Now, where do I look for instructions to configure my ADSL connection? I tried pppoeconf, it gives some error messages "could not open.." and exits.

Regards,
netnut.

Can you give me more information re: your ntfs partition? What is the mount point and what is the problem/error message?

---

### Post by netnut on 2006-08-28
Ok, I will follow your instructions Meng, and start a new thread for ADSL. But, since we're still on it, I cannot access my NTFS partition - Windows D: (hda5) here is the line from the fstab file.
> /dev/hda5   /media/hda5  ntfs  nls=utf8, umask=0222 0	0

And yeah, I have removed those silly mistakes that were there in the fstab (using the same mount point for all the drives!)

And yes, thanks Jareth for the help that you provided... unfortunately I don't have that particular modem - mine is PPPoE, not a USB, thanks a ton anyway.

Regards,
netnut.

---

### Post by bodhi.zazen on 2006-08-29
Try this:
```
/dev/hda5 /media/hda5 ntfs user,auto,rw  0 0
```
in fstab.

---

