---
title: "Ubuntu Mint cannot read 2nd HD"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by Norman Thom on 2006-11-21
Please Help:

I have just installed Ubuntu Mint on my computer.
Seems to work fine.
The problem is I've just added a second drive (slave).
It has Ubuntu 6.10 and I'd like to get some files off it.
The problem is that The Mint OS doesn't seem to read it (both drives are read in the BIOS).  If someone could I'd like to have someone help me either find the 2nd drive on the OS or perhaps suggest some method of getting the OS to read the drive should this not normally happen

---

### Post by aysiu on 2006-11-21
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) should help you.

Though I would stay away from *chmod*ing and *chown*ing anything if you just want to get some files off. You'd be better off with Alt-F2 ```
gksudo nautilus
```

---

### Post by codejunkie on 2006-11-21
> **Norman Thom said:**
> Please Help:

I have just installed Ubuntu Mint on my computer.
Seems to work fine.
The problem is I've just added a second drive (slave).
It has Ubuntu 6.10 and I'd like to get some files off it.
The problem is that The Mint OS doesn't seem to read it (both drives are read in the BIOS).  If someone could I'd like to have someone help me either find the 2nd drive on the OS or perhaps suggest some method of getting the OS to read the drive should this not normally happen
it won't auto detect and mount the drive 
open a terminal and run ```
sudo fdisk -l
``` it will list your drives and partition information, find the partition that is your Ubuntu partition for example /dev/hdb1 now create a mount point for the drive with this ```
sudo mkdir /mnt/ubuntu
```and mount the drive like this ```
sudo mount /dev/hdb1 /mnt/ubuntu
```now you open nautilus and navigate to  /mnt/ubuntu and all your files will be there just make sure you replace /dev/hdb1 with your actual drive partition.

---

### Post by Norman Thom on 2006-11-21
aysiu:

Thanks for the response.  I opened a terminal session and did as you requested.  was asked to put in my password and did, I then got this msg.  (nautilus:11966) libgnomevfs-WARNING *** Failed to open session DBUS connection  Possible causes include . . . (lists some causes I guess).  also ran fdisk-l and both drives are listed.

very puzzled

---

### Post by MetalMusicAddict on 2006-11-21
They do have their own forum you know. ;)

---

### Post by Norman Thom on 2006-11-21
codejunkie:

Thank <you> for your help.
Tried the code you suggested, but with the last command I got this msg.

sudo mount /dev/hdb1/mnt/ubuntu 
mount: can't find /dev/hdb1/mnt/ubuntu in /etc/fstab or /etc/mtab

This disk is correctly identified I think and is indicated as a boot volume also

---

### Post by codejunkie on 2006-11-22
> **Norman Thom said:**
> codejunkie:

Thank <you> for your help.
Tried the code you suggested, but with the last command I got this msg.

sudo mount /dev/hdb1/mnt/ubuntu 
mount: can't find /dev/hdb1/mnt/ubuntu in /etc/fstab or /etc/mtab

This disk is correctly identified I think and is indicated as a boot volume also
run ```
sudo fdisk -l
```in the terminal and post the output here and I'll try and help you get the drive mounted.

---

### Post by bodhi.zazen on 2006-11-22
> **Norman Thom said:**
> codejunkie:

Thank <you> for your help.
Tried the code you suggested, but with the last command I got this msg.

sudo mount [color=red]**/dev/hdb1/mnt/ubuntu**[/color] 
mount: can't find /dev/hdb1/mnt/ubuntu in /etc/fstab or /etc/mtab

This disk is correctly identified I think and is indicated as a boot volume also

Syntax error (typo). You need a space between /dev/hdb1 and /mnt/ubuntu like this:```
sudo mount /dev/hdb1 /mnt/ubuntu
```

---

### Post by D. Y. Lewis on 2006-11-22
Hello, I am new to Linux (just two days!). I have a similar problem, I think.  

My computer says it cannot mount either one of my hard drives when I click on them (places-computer-new volume).  Do I need to just copy and paste the same thing as above, or will it be different in Dapper? 

I am sorry if this is not clear enough or not enough info... I don't really know what you need to know.

Thank you for your time.

---

### Post by bodhi.zazen on 2006-11-22
> **D. Y. Lewis said:**
> Hello, I am new to Linux (just two days!). I have a similar problem, I think.  

My computer says it cannot mount either one of my hard drives when I click on them (places-computer-new volume).  Do I need to just copy and paste the same thing as above, or will it be different in Dapper? 

I am sorry if this is not clear enough or not enough info... I don't really know what you need to know.

Thank you for your time.

Yes.

sudo mkdir <mount_point>
mount <device> <mount_point>

options to enable rw access depend of file system.

Linux native: sudo chmod 777 <mount_point>
[indent]with the file system mounted[/indent]

FAT: use umask=000 in options

NTFS: use ntfs-3g, then umask=000

Also see [fstab](http://ubuntuforums.org/showthread.php?t=283131)

---

