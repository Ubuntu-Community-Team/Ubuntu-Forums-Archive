---
title: "Filesystem troubles"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by berftude_lives on 2007-03-18
Hello,

I'm posting this from a LiveCD, as I am apparently having filesystem trouble.  I don't know what I could have done to bring it about.  Edgy had been running fine for weeks.  I installed Eclipse, browsed the Web a bit, shut the computer down and went to bed.  When I turned it back on, everything mounted read-only.  I get to a prompt, but I can't really do much if I can't write files.

The goal (initially) was to use a LiveCD to research this so I could possibly fool around with fstab and do whatever else to the drive, but it turns out that just mounting it has been an adventure, which bring me to this post.

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdg: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1   *           1          12       96358+  83  Linux
/dev/hdg2              13       19457   156191962+   5  Extended
/dev/hdg5              13         377     2931831   82  Linux swap / Solaris
/dev/hdg6             378       14966   117186111   83  Linux
/dev/hdg7           14967       19457    36073926    b  W95 FAT32
ubuntu@ubuntu:~$ 

```


/dev/hd6 is my root drive, so:

```

ubuntu@ubuntu:~$ sudo mkdir /media/harddisk
ubuntu@ubuntu:~$ sudo mount -t jfs /dev/hdg6 /media/harddisk
mount: wrong fs type, bad option, bad superblock on /dev/hdg6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

That looks correct to me, but what do I know?  After all, I'm posting in the Complete Beginner's forum.  :)  So I try this:

```

ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
[COLOR="Red"]/dev/hdg6 /media/harddisk jfs defaults 0 1[/COLOR]

ubuntu@ubuntu:~$

```

And now,

```

ubuntu@ubuntu:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdg6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ 

```

Ugh.  Okay, let's follow the error message's advice:

```

ubuntu@ubuntu:~$ dmesg | tail -30
[17179665.508000] ppdev: user-space parallel port driver
[17179668.376000] [drm] Initialized drm 1.0.1 20051102
[17179668.432000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKA] -> GSI 12 (level, low) -> IRQ 12
[17179668.432000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179669.972000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179669.972000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17179669.972000] agpgart: Putting AGP V2 device at 0000:01:05.0 into 1x mode
[17179670.392000] [drm] Setting GART location based on new memory map
[17179670.392000] [drm] Loading R300 Microcode
[17179670.392000] [drm] writeback test succeeded in 1 usecs
[17179677.308000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179677.308000] apm: overridden by ACPI.
[17179716.940000] Bluetooth: Core ver 2.8
[17179716.940000] NET: Registered protocol family 31
[17179716.940000] Bluetooth: HCI device and connection manager initialized
[17179716.940000] Bluetooth: HCI socket layer initialized
[17179717.328000] Bluetooth: L2CAP ver 2.8
[17179717.328000] Bluetooth: L2CAP socket layer initialized
[17179718.464000] Bluetooth: RFCOMM socket layer initialized
[17179718.464000] Bluetooth: RFCOMM TTY layer initialized
[17179718.464000] Bluetooth: RFCOMM ver 1.7
[COLOR="Red"][17180685.824000] JFS: nTxBlock = 8192, nTxLock = 65536
[17180705.000000] attempt to access beyond end of device
[17180705.000000] hdg2: rw=0, want=72, limit=2
[17180705.000000] attempt to access beyond end of device
[17180705.000000] hdg2: rw=0, want=128, limit=2
[17180803.372000] attempt to access beyond end of device
[17180803.372000] hdg2: rw=0, want=72, limit=2
[17180803.372000] attempt to access beyond end of device
[17180803.372000] hdg2: rw=0, want=128, limit=2
[/COLOR]ubuntu@ubuntu:~$ 

```

Uh oh.  Well okay, if hdg2 has a problem, let's check it out:

```

ubuntu@ubuntu:~$ sudo fsck -n /dev/hdg2
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/hdg2
Could this be a zero-length partition?
ubuntu@ubuntu:~$ 

```

That sounds even less encouraging.  Back to hdg6, what I've been trying to mount:

```

ubuntu@ubuntu:~$ sudo fsck -n /dev/hdg6
fsck 1.39 (29-May-2006)
fsck.jfs version 1.1.8, 03-May-2005
processing started: 3/18/2007 14.52.4
The current device is:  /dev/hdg6
Block size in bytes:  4096
Filesystem size in blocks:  29296527
**Phase 1 - Check Blocks, Files/Directories, and  Directory Entries
**Phase 2 - Count links
**Phase 3 - Duplicate Block Rescan and Directory Connectedness
**Phase 4 - Report Problems
**Phase 5 - Check Connectivity
**Phase 6 - Perform Approved Corrections
**Phase 7 - Verify File/Directory Allocation Maps
Errors detected in the Fileset File/Directory Allocation Map control information. (F)
Errors detected in the Fileset File/Directory Allocation Map. (F)
**Phase 8 - Verify Disk Allocation Maps
Incorrect data detected in disk allocation structures.
Incorrect data detected in disk allocation control structures.
117186108 kilobytes total disk space.
    13242 kilobytes in 3565 directories.
  2164802 kilobytes in 37340 user files.
        0 kilobytes in extended attributes
    83496 kilobytes reserved for system use.
114951052 kilobytes are available for use.
File system checked READ ONLY.
Filesystem is dirty.
Filesystem is dirty but is marked clean.  In its present state,
the results of accessing /dev/hdg6 (except by this utility) are undefined.
ubuntu@ubuntu:~$ 

```

So I guess this would explain why hd6 is mounting read-only when I boot from the hard drive.  What it does not explain (at least to me) is why I cannot mount this thing from a LiveCD.  It mounts when I boot from it, so maybe I've messed up the commands?

You may have noticed I did the fsck with -n (read-only).  Since I've had less than positive experiences with chkdsk in my years of Windows usage, I'd like to wait for advice on how to proceed.  Thanks in advance for your help; I've found this forum to be a great resource.

---

### Post by inCursorated on 2007-03-18
i'd go ahead and run fsck -av or fsck -v on it from the livecd. back up the data first if you're worried, but it should be fine. i've had filesystems become inaccessible until fsck fixed them up. you can't run fsck on /dev/hdg2 because it's not a filesystem - it's an extended partition that contains logical ones which have individual filesystems. those errors are troubling tho, so maybe u'll want to wait for some better advice as there may be a bigger problem here. ;)

---

### Post by berftude_lives on 2007-03-18
I got to thinking -- my motherboard is a Gigabyte GA-7DXR, which did not initially have support for hard drives larger than 128 GB.  (128 base two, 137 base ten).  I've been using the latest BIOS update (F10) which claims to support hard disks beyond this boundary.  How can I verify that it's actually doing what it's supposed to?

If a drive larger than 128 GB is put into a board that doesn't do 48-bit LBA, write operations loop around to the front of the disk when going beyond the 128 GB boundary.  Those dmesg warnings about falling off the end of the disk sound suspicious.

I don't want to cause groupthink here.  The problem could be something else entirely but I'd like to pursue this as one possible cause...

---

### Post by jallain on 2007-05-31
Did you ever resolve this issue? I have just about the same thing. I, too, have a jfs partiton for root that will not mount on bootup. I tried to run fsck on it but after scanning about half the partition it exits with an error. So far I am unable to fix it. Anybody else experience problems using jfs?

---

### Post by JPorter on 2007-12-02
I've been using JFS with no problems under Gutsy since the release.  Yesterday on a reboot it suddenly mounted read-only and crashed.

Does anyone have an idea of what's going on with this?  I can't run the LiveCD since I have an ATI video chip in my laptop.  I'll try an alternate CD... this sucks.

---

### Post by atlfalcons866 on 2007-12-05
JFS is not really maintained anymore. It is but patches are released once a year. It is maintaned by 1 or 3 guys. IBM has decided not to maintain JFS anymore.

[http://jfs.sourceforge.net/]("http://jfs.sourceforge.net/")

---

