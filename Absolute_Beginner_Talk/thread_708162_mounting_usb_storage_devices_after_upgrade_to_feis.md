---
title: "mounting usb storage devices after upgrade to feisty"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by MichaelSM on 2008-02-26
I've had problems with usb sticks and cameras since edgy>feisty update.

Some time ago I made an entry to /etc/fstab on someone's advice.

Sometimes when I boot up in verbose mode I'm told that line 13 in fstab is bad.

Here's fstab ...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=f6bd7644-46dd-470b-bee2-bf86276e82ad /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=7a072e8d-6c82-4ed8-8add-b1847fa69735 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom2   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /media/sda1  defaults auto rw,user 0 0

What do I need to do?

This should be an easy one.

Thanks in advance,

Mike.

---

### Post by MichaelSM on 2008-02-26
Replying to my own post ....again!

Sorry folks.

My bad.

It wasn't obvious text-wise in gedit, but stood out like dogs' balls in my above post !

For some reason I'd entered into fstab 'sda 1' instead of 'sda1' as in a space where it shouldn't have been.

The camera mounts now, and presumably a usb stick which wouldn't before.

However, 'fstab line 13 is bad' still pops up in verbose boot.

So I still need help.

Thanks to all,

Mike.

PS. Should I delete these posts or leave them for others to 'learn' from? I don't mind being embarrassed and it's not the first time ...

---

### Post by MichaelSM on 2008-03-02
Gee I must love my own company.

The camera mounts perfectly now as I mentioned, and there was a moment of glory when the USB stick did so as well. But the USB stick won't mount now.

The error is bad line 13 in  /etc/fstab

Could someone post how line 13 ought to read? It used to have a 'vfat' entry but I lost the plot and erased it. I put it back in again but got it wrong. Spacing and commas perhaps.

Mistakes are made occasionally.

Thanks in advance,

Mike.

Here's latest /etc/fstab.

# /dev/hda5
UUID=7a072e8d-6c82-4ed8-8add-b1847fa69735  none            swap         sw                          0  0  
/dev/cdrom                                 /media/cdrom0   udf,iso9660  user,noauto                 0  0  
/dev/hdc                                   /media/cdrom1   udf,iso9660  user,noauto                 0  0  
/dev/scd0                                  /media/cdrom2   udf,iso9660  user,noauto                 0  0  
/dev/                                      /media/floppy0  auto         rw,user,noauto              0  0  
/dev/sda1       /media/sda1  defaults  auto rw,user 0 0



/dev/sda1                                  /media/sda1     vfat         users,user                  0  0  

The device is only available to root for writing. This was achieved by installing pysdm from synaptic. Only one step to go....

---

