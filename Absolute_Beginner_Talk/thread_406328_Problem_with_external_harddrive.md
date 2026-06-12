---
title: "Problem with external harddrive"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by dbansal on 2007-04-10
I have a venus ds3 enclosure with a SATA 250gb HD on an NTFS file system and it is not being detected in Ubuntu. 

This is what i get when i put the following commands:

sudo fdisk -l
Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 1 319 2562336 82 Linux swap / Solaris
/dev/hda2 320 956 5116702+ 83 Linux
/dev/hda3 957 7297 50934082+ 83 Linux
lodge@lodge-server:~$


also when I do dmesg i get this:

[109152.182434] usb 2-2: new full speed USB device using uhci_hcd and address 7
[109152.325707] usb 2-2: configuration #1 chosen from 1 choice

I am a total n00b. I just recently installed ubuntu on my desktop. I used this external on my Windows Xp laptop.

Also, when i go into system > administration > device manager the system does detect something. However, this is what it says: Unknown (0xffff). Also, Under the vendor specifications it does detect that it has an Oxford chipset.

Any ideas?!

THANKS!

---

### Post by devnulljp on 2007-04-11
ntfs is not really well supported. You need the right kernel modules.

modprobe ntfs

Try this:

sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

If you want (risky) read-wrte try:

sudo mount /dev/hda1 /media/windows/ -t ntfs -o rw nls=utf8,umask=0222

---

### Post by dbansal on 2007-04-11
Alright well i got my drive mounted!! It seems as though there was something wrong with the connection (DUH!!)

However, I still had to manually edit my fstab.

My fstab looks like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=a190aa94-46a4-4676-9ede-f374b1f8d3aa /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=7f22e723-779e-4cfc-ba53-f83864c0e851 /files/hda3     ext3    defaults        0       2
# /dev/hda1
UUID=d5779f1c-b0ce-470c-9bc5-6e95c0a81a97 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
[COLOR="Red"]/dev/sda1       /media/external ntfs nls=utf8,umask=0222 0 0  [/COLOR]  

However, that directory is still being put as read-only:
[I]lodge@lodge-server:~$ sudo chmod 777 /media/external
chmod: changing permissions of `/media/external': Read-only file system[/I]

When i right click on the folder it says that root can only change properties. When i login as root it says its a read only system.

Any ideas?

---

### Post by dbansal on 2007-04-11
bump

---

### Post by devnulljp on 2007-04-13
You can't use chmod to change permissioons on a mount, you need to do that at mount time
ntfs support is read only
there are ways to mount read-write; you need the -o rw in the mount command

vfat is a better filesystem for an external drive for compatibility sake.

---

### Post by george29 on 2007-04-13
if you want to be able to write to an ntfs partition then you'll need to install the ntfs-3g driver and then modify fstab.

---

