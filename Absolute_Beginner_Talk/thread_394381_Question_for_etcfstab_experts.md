---
title: "Question for /etc/fstab experts"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-03-26
I can't get my PC to recognize blank DVD's. I have two drives. The top (dev/hda) is the writer and the bottom (dev/hdb) is the reader. It will recognize CD's with or without data. It willonly recognize DVD's with data, but not blank ones. I was looking at my etc/fstab file and was wondering since I have one drive that writes CD's and DVD's both, how should it be written? Also, when I look in SYSTEM>ADMINISTRATION>DISKS(disk manager) it shows both drives as CD-ROM, which is not right. They are combo drives. They each either read or write both. How do I fix this so it recognizes it as a CD/DVD burner. By the way, I have a SATA  HD, so my partitions are listed as sda and cd/dvd drives as hda/hdb.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

[ATTACH]28349[/ATTACH]
[ATTACH]28350[/ATTACH]

---

### Post by BrianK on 2007-03-26
your fstab is correct.  I have the same setup as you, though my drives are on the secondary IDE channel, so I get hdc & hdd, but my fstab looks like so:

```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
```

If you're seeing media at all, your fstab is correct.  What makes you say it can't see blank media?  Is your burning program not working?  What are you using?  Does it give an error message or does it do nothing at all?  How much time have you allowed it before re-ejecting the media?

It's possible it's the media itself... maybe your writer only likes DVD-R & you have DVD+R?

---

### Post by 67GTA on 2007-03-26
I am trying to write a DVD ISO image to DVD. I have tried everything. DVD-R, DVD+R, K3B,Gnomebaker, nautilus's right click>write to disc option. I have even tried the command line. Every attempt with all media types gets the error: no media found, or not recognizable as recordable media. I was out of ideas and decided to poke around in the config files. Is it possible for the CD burner to work and not the DVD burner? Are they seperate or the same device? Would dual/single layer DVD's make any difference?

---

### Post by 67GTA on 2007-03-26
When I try to use nautilus's right click>write to disc option it says to insert blank media. It says the supported types are CD-R,CD-RW,DVD-RW,DVD+R,DVD+R DL,DVD+RW. I am trying with DVD+R. Something is not right. Gnomebaker, K3B, and the terminal commands  tell me there is no media detected. I am out of ideas, just fishing now.

---

### Post by halitech on 2007-03-26
it could be a dying drive as I had the same problem just before christmas where my dvd burner would read anything, would sometimes burn +r data dvds but fail when trying to write dvd iso files. K3b, NeroLinux and gnome baker would all say insert blank media.

Hopefully it's not the case with your but may be looking at a hardware purchase in the future :(

---

