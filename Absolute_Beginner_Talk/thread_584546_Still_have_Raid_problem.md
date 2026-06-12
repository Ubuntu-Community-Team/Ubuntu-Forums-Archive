---
title: "Still have Raid problem"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Gone fishing on 2007-10-21
Sorry I originally started this post  in Gutsy development (which is now closed)

The story so far:

I've set up a raid1 on Gutsy server RC, I've go it set up so it works using these instructions: [http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/) (I've set up three raid1 partitions /, /home and swap) The problem is if I test it by disconnecting one of the drives Gutsy wont boot.

If I run the following commands

jhjk@lampserver:~$ grep /dev/md /etc/fstab
# /dev/md0
# /dev/md1
# /dev/md2
jhjk@lampserver:~$

jhjk@lampserver:~$ df -h / /home
Filesystem Size Used Avail Use% Mounted on
/dev/md0 15G 2.6G 12G 19% /
/dev/md1 131G 225M 124G 1% /home

jhjk@lampserver:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : active raid1 sda3[0] sdb3[1]
1991936 blocks [2/2] [UU]

md1 : active raid1 sda2[0] sdb2[1]
138672960 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdb1[1]
15623104 blocks [2/2] [UU]

unused devices: <none>

and

jhjk@lampserver:~$ sudo mdadm --query --detail /dev/md0
/dev/md0:
Version : 00.90.03
Creation Time : Wed Oct 17 00:51:54 2007
Raid Level : raid1
Array Size : 15623104 (14.90 GiB 16.00 GB)
Used Dev Size : 15623104 (14.90 GiB 16.00 GB)
Raid Devices : 2
Total Devices : 2
Preferred Minor : 0
Persistence : Superblock is persistent

Update Time : Wed Oct 17 09:52:49 2007
State : active
Active Devices : 2
Working Devices : 2
Failed Devices : 0
Spare Devices : 0

UUID : 2aa5c0cf:d2ed8c33:31b70149:8694a062
Events : 0.7

Number Major Minor RaidDevice State
0 8 1 0 active sync /dev/sda1
1 8 17 1 active sync /dev/sdb1
jhjk@lampserver:~$

similar results for md1 and md2

So it looks like the Raid is working but if I test it by unplugging a hard drive it wont boot

I've also tried creating a small non Raid /boot partition, but again if I unplug a drive the system wont boot (grub starts fails to mount the raid)

anyone got any ideas or got Raid1 working on Gutsy?

---

### Post by Shr00mSter on 2007-10-23
I'm having the exact same problem you are. Hopefully somebody can figure out a solution, ive been searching for clues on how to fix this all day.

---

### Post by Gone fishing on 2007-10-26
Shr00mSter did you ever find a solution - I've just about given up and am probably going to have to try opensuse :(

---

### Post by Gone fishing on 2007-10-29
I found this on launch pad (Ubuntu Bugs)

[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/120375](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/120375)

 peterh  wrote on 2007-06-14:  (permalink)

Sorry folks, being tooo fast.

This is not working if all discs are present, now i understand the include of MD_DEGRADED_ARGS

my new workaround is to add a bootmenue entry in grub

title Ubuntu, kernel 2.6.20-16-generic (raid defect)
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-16-generic root=/dev/md1 ro raid_degraded
initrd /boot/initrd.img-2.6.20-16-generic

and /etc/initramfs-tools/scripts/init-premount/raid_degraded

#!/bin/sh

set -eu

PREREQ="udev"

prereqs()
{
        echo "$PREREQ"
}

case ${1:-} in
  prereqs)
    prereqs
    exit 0
    ;;
  *)
    . /scripts/functions
    ;;
esac

if [ -e /scripts/local-top/md ]; then
  log_warning_msg "old md initialisation script found, getting out of its way..."
  exit 1
fi

MDADM=$(command -v mdadm)
[ -x $MDADM ] || exit 0

if grep raid_degraded /proc/cmdline 2>/dev/null; then
  echo "MD_DEGRADED_ARGS=' '" >> /conf/md.conf
fi

exit 0

now if a disc is defect and i will to start only with one disc i choose raid defect from bootmenu

This looks like a good work round I haven't tried it, as I only found the work round after I gave up and installed Opensuse :(

---

### Post by Shr00mSter on 2007-10-30
No I'll probably just get a hardware raid card.

---

### Post by Gone fishing on 2007-11-05
Be careful I borrowed a cheep RAID Card and it turned out to be just a fake RAID card just like in some mother boards. The RAID1 setup in Opensuse works fine but it feel slow and less responsive than Ubuntu.

However, the server is up an running :)

---

