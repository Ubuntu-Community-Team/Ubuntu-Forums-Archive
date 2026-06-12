---
title: "usb thumbdrive mount problems"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by the.phantom on 2007-07-07
i made a  old box into a test system.
old/slow with win98 and edgy dual boot
i wanted to import a address book into O.E. but win98 doesn't support my thumb

so as a learning thing, i found this for being able to work the fat32 system
was easy just do this 

> * To mount Windows partition 

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

    * To unmount Windows partition 

sudo umount /media/windows/

so i plugged in the thumb on edgy and copied it to a win folder, rebooted into win98 and got it in

was happy
BUT
now when i plug in my thumb drive edgy doesn't see it
i looked in places and it is not there

this is what fdisk -l shows

Disk /dev/hda: 30.7 GB, 30735581184 bytes
16 heads, 63 sectors/track, 59554 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       28575    14401768+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/hda2           28576       58204    14932417+  83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hda3           58204       59543      674730    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/hda5           58204       59543      674698+  82  Linux swap / Solaris

Disk /dev/sda: 512 MB, 512753664 bytes
16 heads, 32 sectors/track, 1956 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1956      500720    e  W95 FAT16 (LBA)

and this is what fstab shows

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=69d239e2-0366-48cf-8eca-745b0ed39863 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=993daea4-561e-485c-9fbf-147af9f34fc5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

so with all my newbie knowledge i can see it in fdisk, but not in fstab

so can some kind person please tell me what to edit in fstab to get it back working?????

thanks

---

### Post by pbaumgar on 2007-07-07
I don't see /dev/hda1 in your fstab...

---

### Post by the.phantom on 2007-07-07
hda1 is the win partition
and yep it doesn't show but i can mount it
 and 
gksudo nautilus and navigate to media/windows and it is there and i can work it?

as i said i did have the thumb drive working, and did copy a folder to the windows system

but now the thumb drive is not showing up in places nor can i find it !

so any ideas?

with Ubuntu is the only way i can use a thumb drive on that system and i'll go broke burning cd's

so this is what i have in fdisk


what do i need to put in fstab ?????????? i don't care if it shows up on the desktop ( would be nice) just so i can find the thumb drive

---

### Post by p_quarles on 2007-07-07
I had a similar problem the other day. Apparently there's a problem with the most recent kernel initiating the hardware abstraction layer. What worked for me: ```
sudo /etc/init.d/dbus restart
```
After that, the flash drive showed up fine. For whatever reason, it wouldn't *un*mount afterward from the GUI, so I had to do that with root permission from the command line. It has worked as it should since then, though. 

I, too, that at first that I would need to edit fstab, but after a lot of searching, I found that removable devices should *not* be listed there, as you won't be able to unmount them without editing the file. And you really don't want to unplug a flash drive in Linux without unmounting it first.

Hope this works for you.

---

### Post by the.phantom on 2007-07-07
the thumb drive was installed and ran
sudo /etc/init.d/dbus restart

and still no work
but i rebooted and did a hotplug of it and all is back to normal !
thanks !!!!!!!!!!!!!!!!!!!!!!!!!!

---

