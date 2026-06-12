---
title: "Problem with automount and media:/ protocol"
date: 2005-11-06
forum: Apple PPC Users
---

### Post by tiagobt on 2005-11-06
I have a Mac Mini and I use Kubuntu 5.10. Although I have all the upgrades from all repositories (KDE 3.4.3), I still have problems with the media:/ protocol, that is always empty! Besides, when I insert a CD, I get an error saying that there was a mistake while trying to load media:/hdb. After that, several error windows keep popping up and the system becomes very slow. My fstab:

```
proc            /proc           proc    defaults          0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       none            swap    sw                0       0
/dev/cdrom	/media/cdrom	udf,iso9660 user,noauto   0       0
/dev/hda3       /media/mac      hfsplus user,auto         0       0 
```

How can I fix that?

---

### Post by ltmon on 2005-11-06
Hi,

"media:/" in Kubuntu doesn't have a great deal to do with fstab, more so with HAL (hardware abstraction layer).  HAL gets some of it's data from fstab, but also some of it's information from things like UDev and pmount (automounting of usb keys for example).

The popup windows are another system altogether, which is "ivman".  Usually ivman pops up it's windows too quickly, and the media isn't mounted correctly yet.  This is most likely your error source.

Confused yet? :)

Personally I edited the file /etc/ivman/*.xml files to stop all this popping up of windows anyway.  Each of those files has a man page if you want to get advanced about it.  Another way is to just "killall ivman" to stop it altogether.  Search for ivman on these forums for more full descriptions of how to kill/manipulate this thing.

Now that we have the basic terminology down can you try the following:

1. plug in a usb mass storage device (ipod, portable HD, memory key etc)
2. wait maybe 5 seconds (if there's disk activity still, wait some more)
3. type "dmesg | tail" into a terminal
4. post that output here
5. type "lshal > hal_output.txt"
6. post that file "hal_output.txt" here

The "dmesg" command outputs messages from your kernel (the kernel ring buffer to be really precise), and should contain a few new messages when you plug in a device.

The "lshal" command lists all devices that HAL is currently aware of.  We should be able to find your newly plugged device in there. 

Cheers,

L.

---

### Post by tiagobt on 2005-11-07
Thanks a lot, ltmon! For some reason, my USB memory card reader works pretty fine. I inserted the memory stick and, in a few seconds, an icon was created on my Desktop and the correct pop up window was opened (I haven't killed ivman yet). The memory stick was detected as sdd1. The command "dmesg | tail" returned the following:

```
tiago@ubuntu:/etc/ivman$ dmesg | tail
[ 1390.573496] SCSI device sdd: 31680 512-byte hdwr sectors (16 MB)
[ 1390.583457] sdd: Write Protect is off
[ 1390.583462] sdd: Mode Sense: 43 00 00 00
[ 1390.583466] sdd: assuming drive cache: write through
[ 1390.601401] SCSI device sdd: 31680 512-byte hdwr sectors (16 MB)
[ 1390.605385] sdd: Write Protect is off
[ 1390.605389] sdd: Mode Sense: 43 00 00 00
[ 1390.605392] sdd: assuming drive cache: write through
[ 1390.605396]  /dev/scsi/host0/bus0/target0/lun3: p1
[ 1394.148601] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
```

The file hal_output.txt is a way too long and Ubuntu Forums doesn't let me post the entire text. As I don't know what part is important, I'll post the beginning. If you need something else, please tell me. There it goes:

```
Dumping 60 device(s) from the Global Device List:
-------------------------------------------------
udi = '/org/freedesktop/Hal/devices/volume_label_'
  volume.policy.desired_mount_point = 'MS'  (string)
  volume.policy.mount_filesystem = 'vfat'  (string)
  volume.policy.should_mount = true  (bool)
  info.udi = '/org/freedesktop/Hal/devices/volume_label_'  (string)
  info.product = 'MS'  (string)
  volume.size = 16174592  (0xf6ce00)  (uint64)
  volume.num_blocks = 31591  (0x7b67)  (int)
  volume.block_size = 512  (0x200)  (int)
  volume.partition.number = 1  (0x1)  (int)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  volume.is_partition = true  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.mount_point = '/media/MS'  (string)
  volume.label = 'MS'  (string)
  volume.uuid = ''  (string)
  volume.fsversion = 'FAT12'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fstype = 'vfat'  (string)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_USB_Card_Reader'  (string)
  block.is_volume = true  (bool)
  block.minor = 49  (0x31)  (int)
  block.major = 8  (0x8)  (int)
  block.device = '/dev/sdd1'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  info.parent = '/org/freedesktop/Hal/devices/storage_model_USB_Card_Reader'  (string)
  linux.sysfs_path_device = '/sys/block/sdd/sdd1'  (string)
  linux.sysfs_path = '/sys/block/sdd/sdd1'  (string)

udi = '/org/freedesktop/Hal/devices/pmu_info_1'
  info.udi = '/org/freedesktop/Hal/devices/pmu_info_1'  (string)
  linux.hotplug_type = 6  (0x6)  (int)
  ac_adapter.present = false  (bool)
  info.capabilities = {'ac_adapter'} (string list)
  info.category = 'ac_adapter'  (string)
  info.product = 'AC Adapter'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  linux.pmu_type = 1  (0x1)  (int)
  linux.pmu_path = '/proc/pmu/info'  (string)

udi = '/org/freedesktop/Hal/devices/storage_model_MATSHITACD_RW_CW_8124'
  info.addons = {'hald-addon-storage'} (string list)
  storage.policy.desired_mount_point = 'cdrecorder'  (string)
  storage.policy.mount_filesystem = 'auto'  (string)
  storage.policy.should_mount = true  (bool)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_MATSHITACD_RW_CW_8124'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_model_MATSHITACD_RW_CW_8124'  (string)
  storage.cdrom.write_speed = 4233  (0x1089)  (int)
  storage.cdrom.read_speed = 4233  (0x1089)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.dvdplusrw = false  (bool)
  storage.cdrom.dvdplusr = false  (bool)
  storage.cdrom.dvdram = false  (bool)
  storage.cdrom.dvdrw = false  (bool)
  storage.cdrom.dvdr = false  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.firmware_version = 'DACD'  (string)
  storage.requires_eject = true  (bool)
  storage.hotpluggable = false  (bool)
  info.capabilities = {'storage', 'block', 'storage.cdrom'} (string list)
  info.category = 'storage'  (string)
  info.product = 'MATSHITACD-RW CW-8124'  (string)
  storage.removable = true  (bool)
  storage.physical_device = '/org/freedesktop/Hal/devices/pci_106b_3b_ide_0_1'  (string)
  storage.drive_type = 'cdrom'  (string)
  storage.vendor = ''  (string)
  storage.model = 'MATSHITACD-RW CW-8124'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.media_check_enabled = true  (bool)
  storage.no_partitions_hint = true  (bool)
  storage.bus = 'ide'  (string)
  block.is_volume = false  (bool)
  block.minor = 64  (0x40)  (int)
  block.major = 3  (0x3)  (int)
  block.device = '/dev/hdb'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  info.parent = '/org/freedesktop/Hal/devices/pci_106b_3b_ide_0_1'  (string)
  linux.sysfs_path_device = '/sys/block/hdb'  (string)
  linux.sysfs_path = '/sys/block/hdb'  (string)
```

I just want to emphasize that my USB card reader works fine. My problem is with the CD drive.

Thanks again for the help.

---

### Post by ltmon on 2005-11-07
Oh, OK.  It seems from what you've posted that the USB drives and card reader are working fine... am I right.  Is your "media:/" protocol still empty?  It should really be exactly the same as your Desktop.

Also, HAL seems to be quite aware of your CD drive, so that's not the problem.  

Does the CD drive still act crazy once you've killed IVMAN?

What exactly are the error messages you get?

L.

---

### Post by tiagobt on 2005-11-07
You're right, the Memory Stick icon shows up both on the Desktop and on the media:/ protocol. Now the media:/ protocol is no longer empty. It's just that I expected media:/ to show all my partitions, CDs, removable media, etc. But if it's only supposed to show removable media, then I think it's working fine.

Now I killed ivman and inserted a CD-ROM. It seemed nothing had happened at first, but I then noticed that the CD had been mounted in the folder /media/cdrom that I had created before, like fstab said it would. By the way, the /media folder has nothing to do with the media:/ protocol, isn't that right? What I find weird is that no CD icon was created (neither on the Desktop, nor on the media:/ protocol). That bothers me because the Mac Mini has no eject button, meaning I can only eject the CD if I open a terminal and type "eject".

One more thing I can't understand is that, just after I installed Kubuntu, the CD-ROM drive seemed to have been recognized as /dev/hdb, and therefore mounted at /media/hdb. That's what fstab used to show before I edited it and that's the device ivman tried to launch when I'd insert a CD (before I killed it, of course). Is there a reason for that? I don't remember this settings working. That's why I decided to edit fstab so that it would look for the CD at /dev/cdrom and mount it at /media/cdrom. This seems to work (on the fstab side), but I guess KDE no longer controls it in any level. Could that be it?

Thanks once again for all the help.

---

### Post by tiagobt on 2005-11-11
Is there a way of killing ivman definitely? Currently, it's being started every time I turn on the computer.

---

