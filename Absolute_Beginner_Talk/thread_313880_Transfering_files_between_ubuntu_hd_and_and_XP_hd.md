---
title: "Transfering files between ubuntu hd and and XP hd"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by Striker9 on 2006-12-06
My computer is setup with XP (NTFS) on the first hd and ubuntu on the second. What I want to do is transfer files from the NTFS hd onto the the second hd. I tried following the instructions here: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#automountntfs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#automountntfs) but I am unable to find the first hd. How would I go about setting this up? 
thanks for the help

---

### Post by Ocxic on 2006-12-06
"sudo fdisk -l" will give you a list of drives, find the one with NTFS beside it and that'll be your windows drive.
the command to mount the drive is
"sudo mount -t ntfs /dev/hd?? /mount/point -o umask=0222"

change /Dev/hd?? and /mount/point to what you need them to be.

I would recommend that you don't write to the windows drive, as write support is experimental, and could potentially hose your windows install.

There is a windows driver to setup your Linux partitions, I forget what it's called tho.

if you wish to write to the windows drive from Linux, there are how-to's in the tips & tricks forum on how to set it up.

to mount the windows drive automatically when Linux boot's you'll have to add 
```

/dev/hd??		/mount/point	ntfs	umask=0222	0	0

```
to your /etc/fstab file., it's been a while since i used a windows drive, so i might be missing somthing in that line for your fstab.

---

### Post by wildsrv on 2006-12-06
I used the windows driver and it lets you see and use the EXT2 and EXT3 (linux) format. It installs easy and works great. Sorry i'm at work right now and cant remember the name of that driver either. I'm sure if you google it or look around you will find it though. Best of luck

---

### Post by lemonsCC on 2006-12-06
the simple answer would be to pop in the liveCD and open gparted...shrink one of your partitions and make a small FAT32 to transfer files between XP and Ubuntu.

---

### Post by Polygon on 2006-12-06
> **wildsrv said:**
> I used the windows driver and it lets you see and use the EXT2 and EXT3 (linux) format. It installs easy and works great. Sorry i'm at work right now and cant remember the name of that driver either. I'm sure if you google it or look around you will find it though. Best of luck

except i also used that, and it made programs screw up in windows and ubuntu complained about a fs check failing on the drive occasionally  that i wrote on using the ext2 driver for windows

your best bet if you dont want to hose or possibly screw up anything is to have a fat32 drive. All os's have full read and write support for fat32, so its good for sharing between linux/windows.

---

### Post by Get_Ya_Wicked_On on 2006-12-06
> **lemonsCC said:**
> the simple answer would be to pop in the liveCD and open gparted...shrink one of your partitions and make a small FAT32 to transfer files between XP and Ubuntu.

How would I go about giving more room to my Ubuntu partition?

Just resize my windows, and use the free space to resize the ubuntu?

---

### Post by lemonsCC on 2006-12-06
depending on where they are on the drive yes that is basically all you need to do.

---

