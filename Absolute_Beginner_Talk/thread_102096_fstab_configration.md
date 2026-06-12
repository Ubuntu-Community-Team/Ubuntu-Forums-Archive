---
title: "fstab configration"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by bonusiso on 2005-12-11
how can i configre my fstab folder in order to see (whenever i want) my ntfs partition?

---

### Post by fog on 2005-12-11
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions)

---

### Post by canadianwriterman on 2005-12-11
First, you to add the folder "windows" to your **/media** directory. 

Next open a Terminal window and type **sudo gedit /etc/fstab**.

You'll need to add a line like:

**/dev/hda1    /media/windows    ntfs    nls=utf8,umask=o222    0    0**

My Windows drive and partition is **hda1**. Change hda1 to the location of Windows on your system. 

The next time you boot, your Windows drive will appear and be accessible read-only.

---

### Post by bonusiso on 2005-12-11
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/sda5       /media/sda5     ntfs    defaults        0       0
/dev/sda6       /media/sda6     ntfs    defaults        0       0
/dev/sda9       /media/win      vfat    defaults        0       0
/dev/sda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

this is my fstab folder!! i wanna seee my sda5 and sda6
and i m using kubuntu

---

### Post by fog on 2005-12-11
Change these lines:
> /dev/sda5 /media/sda5 ntfs defaults 0 0
/dev/sda6 /media/sda6 ntfs defaults 0 0
like these:
> /dev/sda5 /media/sda5 ntfs nls=utf8,umask=0222 0 0
/dev/sda6 /media/sda6 ntfs nls=utf8,umask=0222 0 0


---

### Post by redgilda on 2005-12-18
hello, hope im not intruding on someone else's thread ;-)

if i want to see all my drives when I boot ubuntu AND be able to read/write/anything do I just have to append all the lines in my fstab with "umask=000" ?am i correct in thinking that?

some of my drives are nfts so i understand its not possible to write on these... right? is there a way to change nfts to fat without losing the data? ;-) I guess id have to back up anyway, but i might have a problem backing up 100 gb... hmm

---

### Post by Sokraates on 2005-12-18
@ redgilda

Her's the typical fstab-entry for an NTFS-partition (assumuing it's hda1):

```
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```

This way you will have read-ony rights.

AFAIK it's not possible to simply convert an NTFS-partition into a FAT one. You'd have to back everything up and then reformat the partition. If it suffices for you to read files, you don't need to convert anything. If not, see if you could make a FAT-partition and then have Windows use this for storing shared files.

---

