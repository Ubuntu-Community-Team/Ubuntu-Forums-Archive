---
title: "linux equivalent to erase or scrub HD?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by rggavubt on 2007-03-22
Is there a equivalent program to windows erase for Ubuntu?  I would like to erase, scurb all unused space on my hard drive.  I am using an Ubuntu only PC with Dapper Drake installed.:confused:

---

### Post by moore.bryan on 2007-03-22
[I]this isn't for your ubuntu disk, is it?  ;-)

try gparted livecd ([http://gparted.sourceforge.net/livecd.php/](http://gparted.sourceforge.net/livecd.php/))
[/I]

---

### Post by laidback on 2007-03-22
> **moore.bryan said:**
> [I]this isn't for your ubuntu disk, is it?  ;-)

try gparted livecd ([http://gparted.sourceforge.net/livecd.php/](http://gparted.sourceforge.net/livecd.php/))
[/I]

Gparted is usually installed with Dapper. System>Administration>Gnome partition manager. 
Remember that you cannot alter partitions that are mounted. Gparted hss an unmount option, so use that before you do anything.

---

### Post by Bachstelze on 2007-03-22
Define "unused space" please...

---

### Post by Campingman on 2007-03-22
There are programs for windows (such as Eraser) which will overwrite any unused space on a drive, anything that has been deleted, (or not as is this case with windows) will be overwritten.  I may be wrong (usually am!) but I do not think that is required with Linux as if a file is deleted it is pretty much gone?

---

### Post by rggavubt on 2007-03-22
> **HymnToLife said:**
> Define "unused space" please...

All the free space on my Linux only harddrive.  Unused space and files that I have deleted.

---

### Post by rggavubt on 2007-03-22
> **laidback said:**
> Gparted is usually installed with Dapper. System>Administration>Gnome partition manager. 
Remember that you cannot alter partitions that are mounted. Gparted hss an unmount option, so use that before you do anything.

This is for my linux only drive.  I don't have Gnome partition manager listed under System>Administration?  If this deletes the whole hard drive this is not what I want.

---

### Post by Campingman on 2007-03-22
Hi
There are some free utilities listed on this site:
[http://www.thefreecountry.com/security/securedelete.shtml](http://www.thefreecountry.com/security/securedelete.shtml)
I am still not really sure they are required with Linux,  can you recover deleted files on ext3 file system?

---

### Post by laidback on 2007-03-23
Sorry, it's Gnome Partition Editor, I'm running 6.06 too so would have expected you to have it. You can install it via synaptic though. But as it's the partition that Linux is on this route is a no go.

Live CD with Gparted :-

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Documentation:-

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by indytim on 2007-03-23
Suggest you download and burn a copy of GParted Live.  Boot to it and cleanup your partitions as required.  Note you may destroy your mbr in the process so might also help to have a handy copy of SuperGrub on hand also (boot LiveCD).

Both of these are in my arsenal of boot recovery utilities irregadless of the ops.

Hope this helps,

IndyTim

---

### Post by johnnymac on 2007-03-23
If you are trying to totally wipe a disk just use shred or dd - you do this from a terminal

Shred Example:
```

shred -vfz -n 100 /dev/hda

```

dd example:
```

dd if=/dev/urandom of=/dev/sdx

```

Both will do a great job at destroying any data you may have on a disk.  From this point they can be repartitioned and reformatted to meet your needs without having to worry about data residue.

---

