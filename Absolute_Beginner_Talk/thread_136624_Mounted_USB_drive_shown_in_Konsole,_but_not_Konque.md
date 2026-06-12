---
title: "Mounted USB drive shown in Konsole, but not Konqueror"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by subtex on 2006-02-26
I've got my UMS mp3 player plugged into my machine (Kubuntu), Konqueror tries to auto display the contents but tells me an error about "meda/sdb1" not being there.

I check dmesg and I see that the drive is mounted as "media/IHP-100" and I can browse it fine via the Konsole.  Yet it does not show up in Konqueror at all.

Is there some way to fix this?

---

### Post by Pragmatist on 2006-02-26
There is under Tools-->Options or Edit-->Preferences in Konquerer something called "File Associations" or something like that.  In that section there is a listing of what Konquerer does for all devices, mounted and unmounted.  I'm not running Konquerer on this machine, or I could be much more specific.

---

### Post by subtex on 2006-02-26
I'm looking at that section, but I['m not seeing how this will help me, since Konqueror doesn't see this media folder at all.

I tried manually adding it to the listing, but it's the same deal.  Konqueror doesn't see the dir "IHP-100" at all, yet it is there when I "ls" from the "/media" dir.

---

### Post by Pragmatist on 2006-02-26
post output of: cat /etc/fstab

---

### Post by subtex on 2006-02-28
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by ltmon on 2006-02-28
Hi,

Kubuntu, like Ubuntu should be using the HAL (hardware abstraction layer) to view all your devices.

Try the following in a terminal:
```
ps aux | grep hald
```

This should output a line giving the process details of the HAL daemon.  If it's not there then that's a problem (an easily fixed one though).

Then try:
```
lshal | less
```
This will give details of all devices HAL can see.  Search for your USB key in the list, and post back.

Also make sure you point konqueror at 'media:/' (notice that "media" is a protocol, like 'http:/', not a place in the filesystem).  See if the device appears there.

L.

---

### Post by Pragmatist on 2006-02-28
If it were me, I would read the man pages for:
```
lshal
``` ```
fstab
``` ```
udev
```

Also I would check out the various configuration files in the** /etc/udev** directory.

fstab is your FileSystem TABle  Until recently, you would make entries in /etc/fstab corresponding to whatever devices you had.  This is what gives permissions as to who can mount the device and several other options. Now there is dynamic device naming.  This dynamic naming is handled by udev.  There is also something called hal (hardware abstraction layer) whose purpose is to make the recognition of devices automatic (thus avoiding the very problem your having :p )  

Here is what I would try first:
1.) create an entry for the camera mount point in /etc/fstab  An example:
 **/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0**
This is obviously for the floppy drive.  You have the device file (/dev/fd0) the mount point (/media/floppy0) the filesystem type (auto means it guesses).  then you have options (rw means read/write; user means anybody can mount it, noauto has to do with whether or not the device is automatically mounted on system startup, the last two have to do with backing up the partition and automatically performing a filesystem check on startup. 0 means it doesn't do those things).  You could google on this to find an exact version corresponding to cameras (for instance, for my ipod, I have an option called "sync" in its fstab entry.  There might be camera specific features that require or benefit from some options in fstab.  Bottom line: I would try this just so that your setup correlates your device with a mount point.

2.) The /etc/udev directory contains "rules" files.  The man file says, 
> On device addition, udev matches its configured rules against the available device attributes to uniquely name the device.
Specifically check out the** /etc/udev/udevfs.rules** file

3.) lshal provides lots of useful information about your devices.  And, as you already know, so does dmesg and typing : ```
tail -f /var/log/messages
```  The plug in the device and watch your terminal for the entry to come up.

Anyway, that is the best I can do for now.  Between the above suggestions, and google ([www.google.com/linux)](www.google.com/linux)), you should be able to solve your problem.  If not, we'll try again. :-D

---

### Post by subtex on 2006-02-28
[QUOTE=ltmon]
Try the following in a terminal:
```
ps aux | grep hald
```[/quote]

Ok, I do that and I see this:
```
hal       7905  0.0  0.7   5160  3856 ?        Ss   20:40   0:00 /usr/sbin/hald
hal       7910  0.0  0.1   1868   596 ?        S    20:40   0:00 hald-addon-acpi
hal       7925  0.0  0.1   1868   632 ?        S    20:40   0:00 hald-addon-stor                          age
hal       8556  0.0  0.1   1868   636 ?        S    20:41   0:00 hald-addon-stor                          age
aaronfg   9011  0.0  0.1   3064   764 pts/1    S+   22:23   0:00 grep hald
```

> 
Then try:
```
lshal | less
```
This will give details of all devices HAL can see.  Search for your USB key in the list, and post back.

I do that and I get this:

```
Dumping 80 device(s) from the Global Device List:
-------------------------------------------------
udi = '/org/freedesktop/Hal/devices/volume_uuid_8CD5_1AEA'
  volume.policy.desired_mount_point = 'ipod'  (string)
  volume.policy.mount_filesystem = 'vfat'  (string)
  volume.policy.should_mount = true  (bool)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_8CD5_1AEA'  (string)
  info.product = 'IPOD'  (string)
  volume.size = 29923568640  (0x6f7956c00)  (uint64)
  volume.num_blocks = 58444470  (0x37bcab6)  (int)
  volume.block_size = 512  (0x200)  (int)
  volume.partition.number = 2  (0x2)  (int)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  volume.is_partition = true  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.mount_point = '/media/ipod'  (string)
  volume.label = 'IPOD'  (string)
  volume.uuid = '8CD5-1AEA'  (string)
  volume.fsversion = 'FAT32'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fstype = 'vfat'  (string)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_iPod'  (string)
  block.is_volume = true  (bool)
  block.minor = 18  (0x12)  (int)
  block.major = 8  (0x8)  (int)
  block.device = '/dev/sdb2'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  info.parent = '/org/freedesktop/Hal/devices/storage_model_iPod'  (string)
  linux.sysfs_path_device = '/sys/block/sdb/sdb2'  (string)
  linux.sysfs_path = '/sys/block/sdb/sdb2'  (string)

```

I can see the ipod there.

As to the "media:/", that's the whole problem I'm talking about.

"media:/" in konqueror only shows my hard drives and cd drive.  But if I "cd /media" from the konsole, I can see the hard drive, cd drive AND the ipod.

---

### Post by Pragmatist on 2006-02-28
You've got nothing to lose by trying an /etc/fstab entry

---

### Post by subtex on 2006-02-28
Ok, so I added this line:

```
/dev/sdb2 /media/ipod auto rw,user,noauto 0 0
```

now in media:/ in konqueror it shows up as Hard Disk (sdb2) Unmounted Hard Disk Volume

If I right click on the drive and choose "Mount" i get a quick error saying only root can do that.

I don't get why this fails.  Ubuntu on my laptop detects the ipod as a drive fine and mounts it, etc.

Why is Kubuntu so different?

---

### Post by Pragmatist on 2006-03-01
try adding yourself to the group that /dev/sdb2 belongs to.  I'm guessing that the group is: **plugdev** You can add yourself to whatever group /dev/sdb2 belongs to by typing as root: ```
gpasswd -a username groupname
```  Then you can type: ```
groups
``` to see what groups you belong to and make sure your now a member of this new group you added.  Now, you won't get the message about needing to be root to mount /dev/sdb2.

Regarding why all of this is the way it is...I can't help you on that :-k 

Read my previous post on my suggestions for further reading.  This may provide some answers.

---

