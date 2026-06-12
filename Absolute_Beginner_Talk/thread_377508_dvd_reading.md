---
title: "dvd reading"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by aa.ivanov on 2007-03-06
Hi!
I'm running Ubuntu 6.10 on a Toshiba A110 and I'm having some troubles with my dvd drive.

Trying to read a dvd disk I'm running in i/o errors. But if I restart the computer with the dvd disk in the drive I can read DVDs. Does anyone have an idea what could be going wrong? 

The drive has no problems working with CDs.

I'm not sure what info to supply about the device, so here is what i found in the output of lshal:
```
udi = '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'  (string)
  linux.subsystem = 'scsi'  (string)
  linux.hotplug_type = 1  (0x1)  (int)
  scsi.type = 'cdrom'  (string)
  scsi.vendor = 'HL-DT-ST'  (string)
  scsi.model = 'DVDRAM GMA-4082N'  (string)
  info.product = 'SCSI Device'  (string)
  info.linux.driver = 'sr'  (string)
  scsi.lun = 0  (0x0)  (int)
  scsi.target = 0  (0x0)  (int)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 1  (0x1)  (int)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'  (string)
  info.bus = 'scsi'  (string)
  linux.sysfs_path_device = '/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0'  (string)

udi = '/org/freedesktop/Hal/devices/storage_model_DVDRAM_GMA_4082N'
  info.addons = {'hald-addon-storage'} (string list)
  storage.policy.desired_mount_point = 'dvdrecorder'  (string)
  storage.policy.mount_filesystem = 'auto'  (string)
  storage.policy.should_mount = true  (bool)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_DVDRAM_GMA_4082N'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_model_DVDRAM_GMA_4082N'  (string)
  storage.cdrom.write_speeds = {'11080', '5540'} (string list)
  storage.cdrom.write_speed = 11080  (0x2b48)  (int)
  storage.cdrom.read_speed = 11080  (0x2b48)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.hddvd = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.dvdplusrdl = true  (bool)
  storage.cdrom.dvdplusrw = true  (bool)
  storage.cdrom.dvdplusr = true  (bool)
  storage.cdrom.dvdram = true  (bool)
  storage.cdrom.dvdrw = false  (bool)
  storage.cdrom.dvdr = true  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.requires_eject = true  (bool)
  storage.hotpluggable = false  (bool)
  info.capabilities = {'storage', 'block', 'storage.cdrom'} (string list)
  info.category = 'storage'  (string)
  info.product = 'DVDRAM GMA-4082N'  (string)
  info.vendor = 'HL-DT-ST'  (string)
  storage.removable = true  (bool)
  storage.physical_device = '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'  (string)
  storage.lun = 0  (0x0)  (int)
  storage.firmware_version = 'PT06'  (string)
  storage.vendor = 'HL-DT-ST'  (string)
  storage.model = 'DVDRAM GMA-4082N'  (string)
  storage.drive_type = 'cdrom'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.media_check_enabled = true  (bool)
  storage.no_partitions_hint = true  (bool)
  storage.bus = 'scsi'  (string)
  block.is_volume = false  (bool)
  block.minor = 0  (0x0)  (int)
  block.major = 11  (0xb)  (int)
  block.device = '/dev/scd0'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'  (string)
  linux.sysfs_path_device = '/sys/block/sr0'  (string)
  linux.sysfs_path = '/sys/block/sr0'  (string)
```

---

### Post by aa.ivanov on 2007-03-09
hmmm!
No one has an idea!? That's bad!

In the meanwhile I came upon something strange in my dmesg info.
When booting with no dvd in drive, I can't read dvds later and I get this:
```
$ dmesg | grep sr0
[17179588.924000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[17179588.924000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[17179606.016000] pktcdvd: writer pktcdvd0 mapped to sr0
[17179897.884000] sr0: rw=0, want=8192128, limit=2097151
[17179897.884000] Buffer I/O error on device sr0, logical block 2048031
[17179897.884000] sr0: rw=0, want=8192132, limit=2097151
[17179897.884000] Buffer I/O error on device sr0, logical block 2048032
[17179897.884000] sr0: rw=0, want=8192136, limit=2097151
[17179897.884000] Buffer I/O error on device sr0, logical block 2048033
[17179897.884000] sr0: rw=0, want=8192140, limit=2097151
```

But when I boot with a dvd media in drive, the previous command returns:
```
$ dmesg | grep sr0
[17179594.668000] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[17179594.668000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[17179629.972000] pktcdvd: writer pktcdvd0 mapped to sr0
```

Is this normal!!?? I don't think it is. What could be the reason? Anyone? Any ideas? Any speculations?

---

### Post by lamalex on 2007-03-09
what kinds of dvds are these? are you trying to play encrypted dvds without any decryption software?

---

### Post by aa.ivanov on 2007-03-10
No. I'm not messing with dvd-video disks so no CSS is involved here. The disks hold backups. Besides I own no dvd video disks so there's no way to test with them. What I have is a couple dvd-r and a couple of dvd+r disks to play with. Some of them are iso9660 only, and some are recorded with both iso9660 and udf structures enbeld in k3b. Most of the medias are recorded on the same device I'm trying to read them with, but I have a couple of disks recorded under windows and they behave in just the same way.

The [first time I came upon this strangeness]("http://ubuntuforums.org/showthread.php?t=362162") I decided that it has something to do with using kernel-386 instead of kernel-generic. But now I'm pretty convinced I was wrong. Being able to read dvds after power on seems now like a result of hibernating my laptop after (re)booting with dvd-media in drive instead of simply shutting it down.

Why on earth is the device reporting different speeds (24x/24x if no dvd in drive, and 62x/62x if dvd in drive)? Can I make linux reinitialize the device without rebooting?

---

### Post by neilmac86 on 2007-10-29
Hi guys, I'm just wondering if you got this problem sorted, my drive doesnt recognise any discs and when i try to open the drive in my computer to see whats in there, it tells me i have a 1/0 device error,

i tried downloading updated drivers....nothing!

please help!

---

