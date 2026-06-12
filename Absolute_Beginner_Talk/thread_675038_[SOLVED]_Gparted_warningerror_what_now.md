---
title: "[SOLVED] Gparted warning/error what now?"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Desperate on 2008-01-22
after dmraid I find my "volume" in Gparted and it is even willing to mount it! then I get this "
mount: /dev/mapper/isw_bccebhcagd_RAID0 already mounted or /media/windows busy "

Any ideas?

EDIT 1
even after doing it all by hand I get;
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x85933d77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29185   234428481    7  HPFS/NTFS************looks hopeful

******but mounting it ? NOPE *********
ubuntu@ubuntu:~$ sudo mount -a
$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda1': Input/output error
If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
**********so I try to mount the device in /dev/mapper     the one that Gparted recognizes too

ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_bccebhcagd_RAID0 /media/windows
mount: /dev/mapper/isw_bccebhcagd_RAID0 already mounted or /media/windows busy


EDIT 2
Now Gparted thinks it is already mounted, but it still doesn't show??  I'm really Desperate :)

---

### Post by sirgogo on 2008-01-23
Hello Desperate,

Are you booting from the gParted LiveCD? If you do not boot from this there can be errors and usually it does not allow you to edit your partitions without doing so. Let me know, so we can find a solution.

---

### Post by Desperate on 2008-01-23
I work from the live CD, I could try to download and burn the gparted cd and see if that works, thanks for the tip. Low in spare time the next days though so I might report back in a few .

Thanks

Richard

---

### Post by Desperate on 2008-01-26
Update: 
Gparted CD will not load, I get to an options menu and tried a few but they all stop after spitting some text and the last line is; opening linux next line CRC error and I'm hung up. downloaded again and burned a new one, same thing :(

Trying at the other end in a Terminal gives me this;
loaded dmraid and ran it  with -av option gives me two, raid0 and raid01 in /dev/mapper/
adjusted fstab and gave it a try
ubuntu@ubuntu:~$ sudo mount -av /dev/mapper/isw_bccebhcagd_RAID0
mount: can't find /dev/mapper/isw_bccebhcagd_RAID0 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo gedit /etc/fstab
ubuntu@ubuntu:~$ sudo mount -av /dev/mapper/isw_bccebhcagd_RAID0
NTFS signature is missing.
Failed to mount '/dev/mapper/isw_bccebhcagd_RAID0': Invalid argument
The device '/dev/mapper/isw_bccebhcagd_RAID0' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around? 

****** so I try raid01
ubuntu@ubuntu:~$ sudo gedit /etc/fstab  ***** change fstab

ubuntu@ubuntu:~$ sudo mount -av /dev/mapper/isw_bccebhcagd_RAID01
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/mapper/isw_bccebhcagd_RAID01': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/mapper/isw_bccebhcagd_RAID01 /media/windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/mapper/isw_bccebhcagd_RAID01 /media/windows ntfs-3g defaults,force 0 0


So what will happen when I choose option 2 as Billy G doesn't cooperate anymore. ??????????

Any hints welcome and have a great weekend anyway :)

Richard

---

