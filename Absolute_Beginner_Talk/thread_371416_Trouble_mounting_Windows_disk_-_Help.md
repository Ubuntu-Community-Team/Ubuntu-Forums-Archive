---
title: "Trouble mounting Windows disk - Help"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Michl on 2007-02-26
I have checked the various directions for doing this,
most helpfully this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

I entered the relevant line with nls=utf8 and without as suggested
in Community DOcs "Make Windows Partition automatically available"

But when I:
     sudo mount -a
I get this message:
     mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
            missing codepage or other error
            In some cases useful info is found in syslog - try
            dmesg | tail  or so

When I go to the file where this is mounted, the file
has no contents, etc.

Perhaps this is relevant:  the info for this disk in fdisk -l is:

     Disk /dev/hdb: 20.4 GB, 20419854336 bytes
     255 heads, 63 sectors/track, 2482 cylinders
     Units = cylinders of 16065 * 512 = 8225280 bytes

        Device Boot      Start         End      Blocks   Id  System
     /dev/hdb1   *           1        2482    19936633+   7  HPFS/NTFS

This is a second hard disk set as slave and the dual boot works perfectly.

I hope someone can help!!

Michael

---

### Post by taurus on 2007-02-26
What's the content of your /etc/fstab then?

```
cat /etc/fstab
```

---

### Post by Michl on 2007-02-27
Here it is:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=16a799e9-264c-43c5-9e60-8f9de7073f59 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=402969d2-f16f-493e-9386-beeb524a8a8e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1 /windows ntfs unmask=0222 0 0


I added the last line, and I tried it as above and also this way:
/dev/hdb1 /windows ntfs nls=utf8,unmask=0222 0 0

Michael

---

### Post by taurus on 2007-02-27
> **Michl said:**
> Here it is:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=16a799e9-264c-43c5-9e60-8f9de7073f59 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=402969d2-f16f-493e-9386-beeb524a8a8e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1 /windows ntfs u**[COLOR="Red"]n[/COLOR]**mask=0222 0 0


I added the last line, and I tried it as above and also this way:
/dev/hdb1 /windows ntfs nls=utf8,u**[COLOR="Red"]n[/COLOR]**mask=0222 0 0

Michael

Okay, you have an extra n in the umask.  You need to edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and remove that n so it would now look like this.

```
/dev/hdb1 /windows ntfs nls=utf8,**umask**=0222 0 0
```

Then, reboot.

---

### Post by Michl on 2007-02-27
> **taurus said:**
> Okay, you have an extra n in the umask. 

Ouch, that hurts. :oops:  I've done this before with umount.  Thank you!  I'm
glad there's a place here for Absolute beginners.  

Ok, this is taken care of.  Now I only need to find out why my modem
keeps cutting out when downloading certain packages with Synaptic 
and why Evolution freezes when I try to set-up an IMAP account and then
I am set.

Michael

---

