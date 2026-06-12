---
title: "fsck pauses bootup"
date: 2010-06-05
forum: Apple Hardware Users
---

### Post by roberto.tomas on 2010-06-05
I'm on lucid on a g5.

fsck has been pausing boot for me at the keys: S to skip, M: to fix manually  -- more or less since I added some removalbe media mount points to fstab:
                                                                                      ```
# /reserva was on /dev/sdd1 during installation: serves as backup
LABEL=reserva /media/reserva ext4    nodev,nosuid,relatime,noauto        0       2
# stuff was /dev/sdc1 on May 2010
LABEL=stuff /media/stuff     ext4    user,nodev,nosuid,relatime,noauto   0       2
# /dev/dvdrw works
/dev/dvdrw  /media/dvdrw     auto    user,auto         0       0
```these discs are fine and fsck finds nothing -- just to be sure I booted to the live cd and fscked everything, including the root and var partitions. everything checks out fine, instantaneously. yet it will hang there, apparently waiting on a disk check. this is the section in var/log/messages at the pause:
```
Jun  5 07:37:39 quad-g5 kernel: [   13.396812] device-mapper: uevent: version 1.0.3
Jun  5 07:37:39 quad-g5 kernel: [   13.397237] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jun  5 07:37:39 quad-g5 kernel: [   13.852305] EXT4-fs (sdb1): mounted filesystem with ordered data mode
Jun  5 07:37:39 quad-g5 kernel: [   15.008253] EXT4-fs (sdb2): mounted filesystem with ordered data mode
Jun  5 07:37:39 quad-g5 kernel: [   18.912527] windfarm: Backside control loop started.
Jun  5 07:37:39 quad-g5 kernel: [   18.993837] windfarm: Slots control loop started.
Jun  5 07:37:39 quad-g5 kernel: [   19.155574] windfarm: Drive bay control loop started.
Jun  5 07:37:40 quad-g5 kernel: [   43.162748] type=1505 audit(1275737860.151:6):  operation="profile_load" pid=955 name="/usr/share/gdm/guest-session/Xsession"
```I was told on [#ubuntu]("irc://irc.freenode.net/#ubuntu") that the problem occurs with macs when removable media is added to fstab -- and that I have to use pmount instead. that surprises me -- it would be a pretty big and apparently undocumented deviation from a standard. is this correct? I cannot set mount options for removable media in fstab?

how can I set these options for my removable media without getting the disc-check  thing interrupting my bootup?

---

