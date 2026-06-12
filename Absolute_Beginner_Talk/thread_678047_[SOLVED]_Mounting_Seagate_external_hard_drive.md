---
title: "[SOLVED] Mounting Seagate external hard drive"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Berean on 2008-01-25
Hi, I've just installed "Gutsy", wanting to get away from the monopoly that is Windows!  I'm completely new to Ubuntu, and don't understand how to do most things.  My Sandisk flash drive mounts normally in all 5 usb ports, but when I try to mount my Seagate 250gb external hard drive in any of the ports there is power going to the device, but it doesn't show up on the desktop.  When I go into system-preferences-hardware information I can see that it says FreeAgent, so Ubuntu (I assume) "sees" the hardware.  How on earth can I get it to recognise this external hard drive so I can access my files?  Please treat me as though I know nothing.  Thanking you for your anticipated help.:confused:

---

### Post by cmnorton on 2008-01-25
1) Enter sudo fdisk -l to see the devices you have:

Here's an example from a 4-year old Pentium IV system with two IDE drives.

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20552055

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4680    37592068+  83  Linux
/dev/sda2            4681        4865     1486012+   5  Extended
/dev/sda5            4681        4865     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x579b42a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19929   160079661   83  Linux

2) sudo mkdir /media/sdb1

This command creates a folder in which your external device will be mounted. Please note, the folder name can be anything reasonable, but usually reflects the device's name:

Here's an example mounted device that corresponds to the fdisk command previously:

cnorton@h2oworks:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             37001804  12478604  22643600  36% /
varrun                 1034080       264   1033816   1% /var/run
varlock                1034080         0   1034080   0% /var/lock
udev                   1034080        68   1034012   1% /dev
devshm                 1034080         0   1034080   0% /dev/shm
lrm                    1034080     35324    998756   4% /lib/modules/2.6.22-14-386/volatile
/dev/sdb1            157566568  27955328 121607260  19% /media/sdb1

This next command example depends on the file system on this external device. I'd look at man mount to see what to use for -t if you have not already formatted the exterenal drive to ext3. 

3) sudo mount -t ext3 /dev/sdb1 /media/sdb1 

If you want this drive every time you boot, the you'll need to put a line into /etc/fstab:

sudo vi /etc/fstab

where vi may be substituted for your favorite text editor

/dev/sdb1 /media/sdb1 ext3 defaults,errors=remount-ro 0 1

---

### Post by Berean on 2008-01-25
Charles, thank you.  However, I've tried doing what you suggested (assuming this is done in the terminal?) and after making a directory it comes up as:

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I don't know what dmesg etc means, or what I have to do with it.  I first used this external hard drive in XP and have all my files on it, so I would prefer not to format it, unless I can go back to XP and save all my files to it again?  When I installed Gutsy it did transfer most files but not all.  Any advice?

---

### Post by Berean on 2008-01-25
I mean Gutsy transferred most files from XP and not the external hard drive!

---

### Post by cmnorton on 2008-01-25
I believe you can mount an ntfs drive? You'll need to look at the output of man mount, or find a Windows PC, and blast these files to a DVD.

I would not format the drive, because it sounds like you have files on it.

---

### Post by buntu_hugenewbie11 on 2008-01-25
I can't seem to mount y ext3 drive either- due to lack of knowledge and computer know how.
I have a few questions about the mount process:
Will  this mount become automatic everytime you plugin the external drive?
Or do you have to mount it manually everytime?

---

### Post by mc4man on 2008-01-25
As I remember back in feisty you had to make a directory and run a command for usb hard drive like such```
 sudo mkdir /media/SEA_DISK

sudo mount -t ntfs-3g /dev/sdc1 /media/SEA_DISK -o locale=en_US.utf8

ls -la /media
```
(sdc1 is with 2 internal hdd's)
But in gutsy you shouldn't have to do anything - just plug it in.  Run dmesg | tail  and post results or go to admin>system log>syslog, scroll to bottom, plug in drive and view results
here is result of plugging in external seagate drive to compare
```
Jan 25 19:46:15 doug-desktop -- MARK --
Jan 25 19:50:45 doug-desktop kernel: [ 2706.948358] usb 5-7: new high speed USB device using ehci_hcd and address 4
Jan 25 19:50:46 doug-desktop kernel: [ 2707.082990] usb 5-7: configuration #1 chosen from 1 choice
Jan 25 19:50:46 doug-desktop NetworkManager: <debug> [1201308646.135564] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_503__SG062705843'). 
Jan 25 19:50:46 doug-desktop kernel: [ 2707.167803] usbcore: registered new interface driver libusual
Jan 25 19:50:46 doug-desktop NetworkManager: <debug> [1201308646.247330] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_503__SG062705843_if0'). 
Jan 25 19:50:46 doug-desktop NetworkManager: <debug> [1201308646.274545] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_503__SG062705843_usbraw'). 
Jan 25 19:50:46 doug-desktop kernel: [ 2707.240598] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jan 25 19:50:46 doug-desktop kernel: [ 2707.240825] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jan 25 19:50:46 doug-desktop kernel: [ 2707.254197] Initializing USB Mass Storage driver...
Jan 25 19:50:46 doug-desktop kernel: [ 2707.254482] scsi4 : SCSI emulation for USB Mass Storage devices
Jan 25 19:50:46 doug-desktop kernel: [ 2707.254809] usb-storage: device found at 4
Jan 25 19:50:46 doug-desktop kernel: [ 2707.254813] usb-storage: waiting for device to settle before scanning
Jan 25 19:50:46 doug-desktop kernel: [ 2707.255221] usbcore: registered new interface driver usb-storage
Jan 25 19:50:46 doug-desktop kernel: [ 2707.255429] USB Mass Storage support registered.
Jan 25 19:50:51 doug-desktop kernel: [ 2712.249566] usb-storage: device scan complete
Jan 25 19:50:51 doug-desktop kernel: [ 2712.252304] scsi 4:0:0:0: Direct-Access     Seagate  External Drive        PQ: 0 ANSI: 0
Jan 25 19:50:51 doug-desktop kernel: [ 2712.254041] sd 4:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
Jan 25 19:50:51 doug-desktop kernel: [ 2712.254908] sd 4:0:0:0: [sdc] Write Protect is off
Jan 25 19:50:51 doug-desktop kernel: [ 2712.254914] sd 4:0:0:0: [sdc] Mode Sense: 27 00 00 00
Jan 25 19:50:51 doug-desktop kernel: [ 2712.254919] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Jan 25 19:50:51 doug-desktop kernel: [ 2712.255908] sd 4:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
Jan 25 19:50:51 doug-desktop kernel: [ 2712.256781] sd 4:0:0:0: [sdc] Write Protect is off
Jan 25 19:50:51 doug-desktop kernel: [ 2712.256785] sd 4:0:0:0: [sdc] Mode Sense: 27 00 00 00
Jan 25 19:50:51 doug-desktop kernel: [ 2712.256790] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Jan 25 19:50:51 doug-desktop kernel: [ 2712.256795]  sdc: sdc1
Jan 25 19:50:51 doug-desktop kernel: [ 2712.277250] sd 4:0:0:0: [sdc] Attached SCSI disk
Jan 25 19:50:51 doug-desktop kernel: [ 2712.277311] sd 4:0:0:0: Attached scsi generic sg4 type 0
Jan 25 19:50:51 doug-desktop NetworkManager: <debug> [1201308651.467979] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_503__SG062705843_if0_scsi_host'). 
Jan 25 19:50:51 doug-desktop NetworkManager: <debug> [1201308651.473961] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_503__SG062705843_if0_scsi_host_scsi_device_lun0'). 
Jan 25 19:50:51 doug-desktop NetworkManager: <debug> [1201308651.507356] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_503__SG062705843_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jan 25 19:50:51 doug-desktop NetworkManager: <debug> [1201308651.597570] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Seagate_External_Drive_SG062705843_0_0'). 
Jan 25 19:50:51 doug-desktop NetworkManager: <debug> [1201308651.681069] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_2AF456E9F456B6B3'). 
Jan 25 19:50:52 doug-desktop ntfs-3g[6189]: Version 1.913 
Jan 25 19:50:52 doug-desktop ntfs-3g[6189]: Mounted /dev/sdc1 (Read-Write, label "SEA_DISK", NTFS 3.1) 
Jan 25 19:50:52 doug-desktop ntfs-3g[6189]: Cmdline options: rw,nosuid,nodev,locale=en_US.UTF-8 
Jan 25 19:50:52 doug-desktop ntfs-3g[6189]: Mount options: noatime,rw,nosuid,nodev,silent,allow_other,nonempty,fsname=/dev/sdc1,blkdev,blksize=4096 
Jan 25 19:50:52 doug-desktop hald: mounted /dev/sdc1 on behalf of uid 1000

```
read and write privileges are automatic for ntfs drive
don't have an ext3 external to test

---

### Post by Desperate on 2008-01-25
Not held back by any knowledge Desperate wrote.

install NTFS-config and it might just read the disk as is. 
System-Administration- software sources and mark Universe and download the data.
then System- Administration-Synaptic P M and search for NTFS-config mark it for installation and when that's finnished look under Applications-System tools

I hope it works for you

Richard

---

### Post by Berean on 2008-01-26
Thanks for all your advice, but I'm having another unrelated problem at present, perhaps due to an upgrade install and not a clean install.  Awaiting a CD for the install.  I'll follow up once I've completed the install, and attempted adding the hardware.  Thanks once again.

---

### Post by lukem on 2008-01-27
I was able to get my Seagate external USB HD to mount using the information in the original post by cmnorton.  I have just upgraded to Gutsy.  In my previous version of Ubuntu this drive would mount automatically whenever it was plugged in, just like a thumb drive.  I would like to restore that capability.  Any ideas?  By the way, thumb drives do mount automatically...

Thanks
Luke

---

### Post by mc4man on 2008-01-27
By default gutsy installs ntfs-3g, libntfs3g12, and fuse-util. You should be able to just plug your external hdd in and have it auto mount with read, write permisions
Did you do a fresh install or upgrade from feisty with update manager?

only in regard to ntfs external drives

---

### Post by lukem on 2008-01-27
I did a fresh install, but the drive is fat32.  I can mount it manually by

sudo mount -t vfat /dev/sda1 /media/sda1

but it still does not appear on the desk top.  I must open it with nautilus.

Thanks
Luke

---

### Post by bigj2632 on 2008-01-28
there is a graphical front end for mounting devices on ubuntu 7.10, i cannot remeber if it comes pre installed or whether i installed it.  i want to say it is called drive mount or something along those lines, you might look in synaptic and unfortunately i am in windows at the moment and cannot remeber.  If you don't find it let me know and i will find boot over.

---

### Post by lukem on 2008-01-28
There was KwikDisk a KDE utility that sounds pretty good.  I might check into PySDM also.  Did not see Drive mount however.

---

### Post by sammydadams on 2008-01-30
if you are still looking at this, Berean (and anyone else having this problem)
i had the same exact problem! i might have a solution for you:

open terminal:
type 

```
fdisk -l 
```

and look for your external...mine shows up as /dev/sdb1 and and it is still ntfs so windows and ubuntu can play nicely together

should be: 

sudo mount -t ***filesystem type*** /dev/sdb1 /media/sdb1 

i think yours is saying wrong fs because you copied what CMNorton wrote...
try:

```
sudo mount -t ntfs /dev/sdb1 /media/sdb1 
```

now it might give you an error saying it was not previously unmounted where you can add -o to the end of it or such, but i am a windows user probably like yourself, so if it gives you that error, try to boot up windows and actively unmount the drive through windows

then reboot Ubuntu and retry...i don't think any of the other guys who really know linux well are going to have this problem since they probably use linux exclusively (and i applaud you guys cause i'm still learning) and wouldn't encounter this type of problem...it seems if windows doesn't shut down the drive nicely, linux can't mount it.  

hope this helps.

---

### Post by sammydadams on 2008-01-30
i forgot to add that you might need to restart hal (this is what mounts your drives i think correct me if i'm wrong anyone) with:

```
sudo /etc/init.d/hal restart
```

also this does not resolve the spindown problems that seem to plague freeagent drives

you might try this for that problem:

[http://ubuntuforums.org/showthread.php?t=679228]("http://ubuntuforums.org/showthread.php?t=679228")

---

### Post by Berean on 2008-02-07
> **sammydadams said:**
> i forgot to add that you might need to restart hal (this is what mounts your drives i think correct me if i'm wrong anyone) with:

```
sudo /etc/init.d/hal restart
```

also this does not resolve the spindown problems that seem to plague freeagent drives

you might try this for that problem:

[http://ubuntuforums.org/showthread.php?t=679228]("http://ubuntuforums.org/showthread.php?t=679228")

Sammydadams,  your advice has worked a treat! Many thanks indeed.  This is the first problem (big) that I've rectified, so I appreciate yours (and the others) advice.  Kind regards,

Berean

---

### Post by vkennedy85 on 2008-04-11
Hey guys, I'm finally taking the plunge on my primary computer.  I've set up Ubuntu to dual boot (until I was sure I had things set up so that I could live without Windows.  I have a 500 gB Seagate as well and am trying to get it recognized.

I opened up the System Log and it seems that it mounts, but I don't know how to navigate to it (through the terminal or GUI).  This is the system log.
```

Apr 11 00:40:40 vince-laptop kernel: [ 2397.604000] usb 5-1: new high speed USB device using ehci_hcd and address 4
Apr 11 00:40:40 vince-laptop kernel: [ 2397.752000] usb 5-1: configuration #1 chosen from 1 choice
Apr 11 00:40:40 vince-laptop kernel: [ 2397.820000] scsi3 : SCSI emulation for USB Mass Storage devices
Apr 11 00:40:45 vince-laptop kernel: [ 2402.820000] scsi 3:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100D PQ: 0 ANSI: 4
Apr 11 00:40:53 vince-laptop kernel: [ 2402.828000] sd 3:0:0:0: [sdb] Spinning up disk....ready
Apr 11 00:40:53 vince-laptop kernel: [ 2410.272000] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Apr 11 00:40:53 vince-laptop kernel: [ 2410.272000] sd 3:0:0:0: [sdb] Write Protect is off
Apr 11 00:40:53 vince-laptop kernel: [ 2410.276000] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Apr 11 00:40:53 vince-laptop kernel: [ 2410.276000] sd 3:0:0:0: [sdb] Write Protect is off
Apr 11 00:40:53 vince-laptop kernel: [ 2410.276000]  sdb: sdb1
Apr 11 00:40:53 vince-laptop kernel: [ 2410.316000] sd 3:0:0:0: [sdb] Attached SCSI disk
Apr 11 00:40:53 vince-laptop kernel: [ 2410.316000] sd 3:0:0:0: Attached scsi generic sg2 type 0
```

If someone could let me know what to do I'd appreciate it, thanks!

---

