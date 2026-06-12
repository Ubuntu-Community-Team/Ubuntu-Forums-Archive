---
title: "read only drives mistake?"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by EddieA on 2006-09-04
Somehow the access to my drives has been made 'root' only and when I gksudo in nautilus I am told I cannot change properties (even as root) as they are 'read only ' ***disks*** 

( these are my two hard drives one mounted as /mnt/ a USB data drive FAT32, and the other as hda1 which holds Winxp, ubuntu is on a partition of this,(hda2).) 

Yet when i do 'mount' in konsole it tells me these discs are (rw)

Can anyone tell me how to make these diska read/write?

---

### Post by monktbd on 2006-09-04
you will need to change some settings in the /etc/fstab file.

check [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
for some explanations :).

edit: if winxp is on an ntfs partition it is rsiky to enable write support because it is not stable yet and can mess up your drive there.

---

### Post by EddieA on 2006-09-04
Thanks for link will check it out - this problem has been plaguing me for days as I can't acces my main data drive

---

### Post by EddieA on 2006-09-04
OK I've read this and will follow your advice and not read/write ntfs win xp partition  but (and this may be a real beginners question) there is no reference in fstab to my USB drive Fat32 HDD which is where my data is kept and I cannot write to this as it is 'read-only' so I can't even change permissions - how can I fix this?
TIA

---

### Post by monktbd on 2006-09-04
there is an option in your system menu about removeable media.
there you can set up how it should be handled.

my fat32 usb partition gets mounted as read/write, so i think you can set it soemwhere there.

it is possible to have an entry for that as well in the /etc/fstab file but it is better to let ubuntu handle it automatically.

if you cannot find the entry in the system menu try
gnome-volume-manger
from the console.
(i have no ubuntu here right now to check it :))

---

### Post by EddieA on 2006-09-04
monktbd - thanks so far - nothing in 'system/removable drives' seems to apply.

When I do 'mount' at the console i get this:

'/dev/sde1 on /media/USB HDD type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)'

which to me is as clear as mud.

 The problem is that somewhere it is marked as a '*read only **disk**'* despite the fact that root has read/write permissions on it's properties root cannot write to it.

Curiouser and curiouser.

---

### Post by monktbd on 2006-09-04
hmmm the mount options are correct (they are at least the same as mine).

the only thing i can think of is now the user and group ids.

are you logged in as the user who setup the system?

is your username listed with uid=100 and gid=100?
the command 
> 
id
shows you that.

---

### Post by EddieA on 2006-09-05
Yes that's ok too

I fixed another problem which related to the rw of my user folder 
see thread:  [Srange start up message]("http://www.ubuntuforums.org/showthread.php?t=250537")
- since I fixed it (and without modifying anything else!) the permissions on usb HDD have changed from root to my group rw and me rw but it still won't let me write - it is still saying:
when I try to change permissions;
"Couldn't change the permissions of "USB HDD" because it is on a read-only disk" 
and  when i try to write anything else to disk; 
"you do not have permissions to write to this folder."
So I am stuck - unless something somewhere is telling my system that this is a cd-type disk.
There are three icons created by Ubuntu linking to this drive they are : 
on my desktop, under 'computer:/// ' and under 'media/'. 
When i right-click the 'media,' link all appears normal for a folder when I right-click either of the others at the bottom of the menu it gives the option to 'eject'which is not applicable to a HDD.
Is yours the same or is this a clue?? (or am I getting desperate :)

---

### Post by monktbd on 2006-09-05
hmmmm i have not much of a clue either...

try a > lsusb on the console and paste the results here.

edit: and also go to the disk on the console make an
> ls -a
and paste the results....

mine looks like this:

> 
drwx------  3 joedoe joedoe 16384 1970-01-01 01:00 .
drwxr-xr-x 26 root root  4096 2006-09-05 06:15 ..
drwx------  2 joedoe joedoe 16384 2006-09-04 21:40 .Trash-joedoe 


(yes it is empty... i dont use the vfat part of my usb harddisk yet)

it means: the current directory is owned by joedoe and he has all rights (rwx)
the one level up directory (media) is owned by root who has all rights and the root group and others have execute (means to be allowed to change into that directory) and read rights.
the trash file is again owned by joedoe.


a
> touch test.txt
changed it to

> drwx------  3 joedoe joedoe 16384 2006-09-05 12:22 .
drwxr-xr-x 26 root root  4096 2006-09-05 06:15 ..
-rwx------  1 joedoe joedoe 0 2006-09-05 12:22 test.txt
drwx------  2 joedoe joedoe 16384 2006-09-04 21:40 .Trash-joedoe 


so it created the empty test file

---

### Post by monktbd on 2006-09-05
another thing:
maybe it gets mixed up by the label name with the space in it?

you can change the label of a fat32 harddisk with mtools.
[http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/](http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/)

---

### Post by EddieA on 2006-09-05
As requested:
Bus 005 Device 007: ID 0ccd:0039 TerraTec Electronic Gm                     bH
Bus 005 Device 006: ID 0402:5635 ALi Corp.
Bus 005 Device 005: ID 0471:082c Philips
Bus 005 Device 004: ID 0471:0829 Philips
Bus 005 Device 002: ID 050d:0237 Belkin Components
Bus 005 Device 001: ID 0000:0000
Bus 007 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 004 Device 002: ID 046d:c51a Logitech, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 002: ID 06a3:8020 Saitek PLC
Bus 001 Device 001: ID 0000:0000
I have 2 usb cards and  old 1.1 usb internal ports
USB mouse, card reader, hub, HDD ,DVD RW, Video(terratec), keyboard
The relevant devices are items 2 & 3 (004 and 005)above one of which is a DVD RW the other USB HDD.

There is no entry for this device in fstab - should there be?
BTW - thanks for your help - I'd have gone potty by now otherwise.

---

### Post by monktbd on 2006-09-05
> **EddieA said:**
> 

There is no entry for this device in fstab - should there be?
BTW - thanks for your help - I'd have gone potty by now otherwise.

that's what i call extensive use of usb :).

i dont think it will make any difference because the drive gets recognized properly but you could try to unplug other usb devices to test the harddisk.

another try would be to search in 
lshal
for the drive and post the properties here.
i am not sure it will help but because you said it might get recognized as a cdrom:
> 
 info.product = 'External HDD'  (string)
  usb_device.product = 'External HDD'  (string)
  info.vendor = 'Western Digital Technologies, Inc.'  (string)
  usb_device.vendor = 'Western Digital Technologies, Inc.'  (string)

 usb.vendor = 'Western Digital Technologies, Inc.'  (string)
  usb.product = 'USB Mass Storage Interface'  (string)


is what i find in lshal - among other things - about my external hdd.
lshal produces HUGE output so it is not really easy to search properly.

> 
lshal > hal.txt
gedit hal.txt

in your home directory should do it.
but then i am not sure it will get us closer to the problem's core.

maybe the renaming as sugggested above could help.

---

### Post by EddieA on 2006-09-05
Well you certainly gave me some work here :)
Only been in Linux since June (Dapper) so these commands are all new.

Didn't use mtools (faint-hearted) Went into you-know-where (as it was a fat32) to change the labeL (I know but I'm getting there):) 

ls -a just gave directory names; ls -a -l (had to look it up) gave me :
> drwx------ 16 ea ea 32768 1970-01-01 01:00 .
drwxrwxr-x  6 ea ea  4096 2006-09-05 15:03 ..
drwx------ 10 ea ea 65536 2006-08-27 10:27 Music
drwx------  9 ea ea 32768 2006-08-27 10:26 Photos
drwx------  6 ea ea 32768 2006-07-05 08:59 Programming
dr-x------  3 ea ea 32768 2006-06-08 15:56 Temp
drwx------  8 ea ea 32768 2006-05-26 12:57 Video

etc for each folder - all appears as it should 
next
> touch test.txt
gave
> touch: cannot touch `test.txt': Read-only file system

> that's what i call extensive use of usb .
This is because I had 128 MB RAM 20GB HDD,no dvd RW,dead cdr, USB 1,  and had to upgrade it all so I put RAM and USB 2.0 Card inside and everything else ouside (USB) so when I buy a new PC (for Linux) I can just plug it all in.

Done lshal (this isn't in my reference book - can you tell me what it is?)

> udi = '/org/freedesktop/Hal/devices/volume_uuid_116D_16F2'
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'utf8', 'shortname=', 'codepage=', 'iocharset=', 'umask=', 'dmask=', 'fmask=', 'uid='} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-system-storage-mount', 'hal-system-storage-unmount', 'hal-system-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  volume.ignore = false  (bool)
  volume.policy.desired_mount_point = 'USBHDD'  (string)
  volume.policy.mount_filesystem = 'vfat'  (string)
  volume.policy.should_mount = true  (bool)
  volume.policy.mount_option.quiet = true  (bool)
  volume.policy.mount_option.iocharset=utf8 = true  (bool)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_116D_16F2'  (string)
  volume.partition.msdos_part_table_type = 12  (0xc)  (int)
  info.product = 'USBHDD'  (string)
  volume.size = 250056705024  (0x3a388a8400)  (uint64)
  volume.num_blocks = 488392002  (0x1d1c4542)  (int)
  volume.block_size = 512  (0x200)  (int)
  volume.partition.number = 1  (0x1)  (int)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  volume.is_partition = true  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_mounted = true  (bool)
  volume.mount_point = '/media/USBHDD'  (string)
  volume.label = 'USBHDD'  (string)
  volume.uuid = '116D-16F2'  (string)
  volume.fsversion = 'FAT32'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fstype = 'vfat'  (string)
  storage.model = ''  (string)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_HDT72252_5DLAT80_00304162'  (string)
  block.is_volume = true  (bool)
  block.minor = 65  (0x41)  (int)
  block.major = 8  (0x8)  (int)
  block.device = '/dev/sde1'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_HDT72252_5DLAT80_00304162'  (string)
  linux.sysfs_path_device = '/sys/block/sde/sde1'  (string)
  linux.sysfs_path = '/sys/block/sde/sde1'  (string)


You're a brave peron!

---

### Post by monktbd on 2006-09-05
> **EddieA said:**
> Well you certainly gave me some work here :)


it is always good to get some command line experience :-D.


> 
Didn't use mtools (faint-hearted) Went into you-know-where (as it was a fat32) to change the labeL (I know but I'm getting there):) 

perfectly fine.

i see you changed it already according to the lshal output (deleted the space).

> 
ls -a just gave directory names; ls -a -l (had to look it up) gave me :


sorry. i made an alias for ls -l to ll and almost only use that so i forogt about the -l
great job on looking it up :).


and yes the permissions really look fine.

> 
Done lshal (this isn't in my reference book - can you tell me what it is?)


hal is the hardware abstraction layer. and ls lists its contents.
the hal is kinda the layer between the OS and the hardware itself. lshal gives a lot of information about all the devices in your system.

and the information is the same as mine actually.

interesting is only that ea is the owner of the /media folder.
did you change that?
and i guess you are logged in as ea.

otherwise i am a bit out of clues now....:-k 



You're a brave peron![/QUOTE]

---

### Post by EddieA on 2006-09-05
> interesting is only that ea is the owner of the /media folder.
did you change that?
and i guess you are logged in as ea.

I probably changed that in an earlier attempt to solve this problem.

Well I don't know where to go from here so I'll have to ponder it a bit.
At the moment I've got a 250GB data drive that I can only read from :( 

I am really grateful for your help and perseverance with this problem. If I ever get it solved I'll send you a private message if that's OK.

All the best.
Eddie

---

### Post by monktbd on 2006-09-05
ok another idea ;).

set up a new user and log in with that.
system-> administration->users and groups

the disk should be automounted with the uid and gid of the new user (probably 1001)
if the problem is still there it is surely not related to your user but somewhere in the system.

---

### Post by EddieA on 2006-09-06
Hello Again monktbd

> **monktbd said:**
> ok another idea ;).

set up a new user and log in with that.
system-> administration->users and groups


OK did it -  same
Also unplugged USB rebooted replugged - same.
edit:searched forums, world and subconscious (Google failed on last one)
Found 'dmsg':
Rebooted, unplugged, replugged did 'dmsg' got:

> [17185500.164000] usb-storage: device found at 10
[17185500.164000] usb-storage: waiting for device to settle before scanning
[17185509.816000]   Vendor: HDT72252  Model: 5DLAT80           Rev: V44O
[17185509.816000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17185509.816000] SCSI device sde: 488397168 512-byte hdwr sectors (250059 MB)
[17185509.816000] sde: assuming drive cache: write through
[17185509.820000] SCSI device sde: 488397168 512-byte hdwr sectors (250059 MB)
[17185509.820000] sde: assuming drive cache: write through
[17185509.820000]  sde: sde1
[17185509.844000] sd 5:0:0:0: Attached scsi disk sde
[17185509.844000] sd 5:0:0:0: Attached scsi generic sg5 type 0
[17185509.848000] usb-storage: device scan complete
[17185511.876000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17185515.036000] FAT: Filesystem panic (dev sde1)
[17185515.036000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[17185515.036000]     File system has been set read-only

(see the last line?) 
Is this it if so what is it?:(

---

### Post by kerry_s on 2006-09-06
It looks to me like your fat file system is corrupt, if you can access it from windows and have the space copy the stuff off the drive and format it then put your stuff back on.

---

### Post by monktbd on 2006-09-06
yeah that might fix it.
because it was recognized properly i didnt think it was necessary to look at the actual system messages while detecting the drive.

hopefully you have some place to backup and reformat.

glad that there is finally some known error.

---

### Post by EddieA on 2006-09-09
Thanks you both 
sorry i'm so late getting back - been spending my spare time backing up 200GB to DVDs (only media available).
I hope this is the solution - but I'll be able to repartition this drive anyway.
Thanks again.

---

