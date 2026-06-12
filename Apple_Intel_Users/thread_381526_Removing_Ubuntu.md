---
title: "Removing Ubuntu"
date: 2007-03-11
forum: Apple Intel Users
---

### Post by Aemelica on 2007-03-11
How to remove ubuntu from my Mac Pro? Is there some type of linux partitioning tool that can change my linux fs's to extended because MacOSX can't read the ext3 partitions and won't overwrite or reformat them. 
Also, what about lilo and refit? Do those need to be removed as well (if so, how?)

Thanks in advance!

---

### Post by Gen2ly on 2007-03-11
> **Aemelica said:**
> How to remove ubuntu from my Mac Pro?

uh, the short answer is yes. deleting an OS is a short and, usually, uncomplicated process.
> Is there some type of linux partitioning tool that can change my linux fs's to extended...

yes, the LiveCD is the best way to do it.  It has many tools to format all types of partitions
> ... because MacOSX can't read the ext3 partitions and won't overwrite or reformat them.

What do you mean?  If you are using ext3 now, that is extended and a very very reliable.  If you're trying to mount an ext3 on Mac OSX there is a program that will do it.  Unfortunately the name illudes me.

> Also, what about lilo and refit? Do those need to be removed as well (if so, how?)

Pudding and crumbs.  lilo lies on ubuntu, u erase that...  rEFIt is a bootloader.  If you plan to install another OS you'd better save it.

Now a little sage dapping.  I spend tons of time installing a new OS just to have the settings as I need it.  Anything you want to have vaulted?

---

### Post by ouilsen on 2007-03-11
IMO do not use the ext3 drivers for Mac OS X. It was unstable here and caused kernel panics.

Just delete your Linux parition with Disk Utility, remove rEFIt ([link]("http://refit.sourceforge.net/doc/c1s3_remove.html")). Now the tough part. Resize a hfs+ partition. There's a commercial program, but fortunately an Ubuntu user had the same problem for a different purpose: [link.]("http://www.ubuntuforums.org/showthread.php?t=89960&highlight=resize+hfs")

---

### Post by stchman on 2007-03-12
> **Aemelica said:**
> How to remove ubuntu from my Mac Pro? Is there some type of linux partitioning tool that can change my linux fs's to extended because MacOSX can't read the ext3 partitions and won't overwrite or reformat them. 
Also, what about lilo and refit? Do those need to be removed as well (if so, how?)

Thanks in advance!

I thought all unix/linux OSs can read ext3.  I think OS X uses HFS but I thought could read ext3.

---

### Post by cyberdork33 on 2007-03-12
there is a driver for OSX to mount ext2/3 filesystems. It is a bit buggy though.

---

### Post by sedatg on 2007-03-12
> **ouilsen said:**
> IMO do not use the ext3 drivers for Mac OS X. It was unstable here and caused kernel panics.

Just delete your Linux parition with Disk Utility, remove rEFIt ([link]("http://refit.sourceforge.net/doc/c1s3_remove.html")). Now the tough part. Resize a hfs+ partition. There's a commercial program, but fortunately an Ubuntu user had the same problem for a different purpose: [link.]("http://www.ubuntuforums.org/showthread.php?t=89960&highlight=resize+hfs")

I believe you don't need to get a commercial app.
The included diskutil command line tool should be able to resize a hfs+ partition IF you were already able to delete the superfluous partitions.

1. Fire up single user mode (while rebooting before the splash screen press cmd+S i believe).
- A command line will show up, wait a while and read the last part carefully.
- It will say somehting about how to initiate a bare bones os x session:
2. Notice it, read it, type it, press enter.
- Wait while you supposedly get a more functional environment.
- After this is done, here's the real thing (these are console commands... beware of typos in my post as this is all somewhat written down from my memory, without checking for correctness!!!):
3. diskutil list
4. diskutil resizeVolume disk0s2 limits (replace disk0s2) with the line from you hfs+ mac hd parition, may differ from mine... not sure and i don't really care either :p )
5. diskutil resizeVolume disk0s2 71G (replace 71 with the output from the previous command)
- Have patience while it goes to work.
- You're done.

Not sure if this acutally works, but trying it should nor kill your system, nor puppies...
Pretty straightforward really. Blame my crappy e-english if it seems somewhat daunting.

Cheers ;)

---

