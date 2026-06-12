---
title: "Dapper won't identify free space for installation"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Halfling Rogue on 2007-06-11
I'm trying to install Dapper on an IBM ThinkPad A20m. I was able to install 5.04 with no problem, and when running it says that I have 8.7 GB of free space. In computer:/// there's the Floppy Drive, the CD/DVD-ROM Drive, and Filesystem.

But when I run the Dapper CD, it says I've only got 13.5 MB of free space, and in computer:/// there's Floppy, CD/DVD, Filesystem, and a fourth one that says 10.9 GB Volume. It won't mount the volume because it says it isn't removable (error: device /dev/hda1 is not removable; error: could not execute pmount), but as long as I can't access it I don't have enough space to install Dapper.

I have no idea why 5.04 uses the space just fine and 6.06 partitions it for whatever reason. Is there a way around this?

---

### Post by Halfling Rogue on 2007-06-11
As instructed to [here]("http://www.linuxquestions.org/questions/showthread.php?p=2603828#post2603828"), ran sudo fdisk -l and got this:

> Disk /dev/hda: 12.0 GB, 12068904960 bytes
255 heads, 63 sectors/track, 1467 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

      Device Boot          Start       End            Blocks    Id     System
/dev/hda1    *                   1       1421     11414151    83    Linux
/dev/hda2                    1422      1467         369495     5     Extended
/dev/hda5                    1422      1467         369463+  82    Linux swap / Solaris


And as [here]("http://www.linuxquestions.org/questions/showthread.php?postid=1810048"), running mount got me

> mount: can't find /dev/hda1 in /etc/fstab or /etc/mtab

But I can't understand the rest of what's in the thread enough to figure out how to fix it, since I wiped my Windows partitions when I installed 5.04. So evidently I've still got a partition somewhere I'm not supposed to.

---

### Post by Halfling Rogue on 2007-06-11
Okay! So, in the Gnome Partition Editor, I've got hda1, hda2, and hda5. 2 is extended filesystem, 360.84 MB. 5 is linux-swap filesystem, 360.81 MB. 1 is ext3 filesystem, 10.89 GB, 1.64 GB used and 9.25 GB unused, with a boot flag. Should I try to move it, or format it to linux-swap, or what?

---

### Post by Halfling Rogue on 2007-06-11
On 5.04 the fdisk -l command returns the exact same info as on Dapper. The mount command returns "mount: /dev/hda1 already mounted or / busy
mount: according to mtab, /dev/hda1 is already mounted on / "

/etc/mtab has "/dev/hda1 / ext3 rw,errors=remount-ro 0 0" for the first line.

/etc/fstab has "/dev/hda1           /        ext3
defaults,errors=remount-ro 0                  1
/dev/hda5                      none             swap     sw
0          0" for the 7-10th lines.


**ETA:** Running "sudo mount /dev/hda1 / " in Dapper mounted the volume and it's now showing up in mtab, but not fstab, and Filesystem is still stating it's only got 13.2 MB of space. In the Gnome Partition Editor it's saying 10.87 GB of hda1 is now being used, but if I try to disactivate hda5 (the linux-swap) it says it "Cannot allocate memory".

**ETA2:** Running "mount /dev/hda1" in Dapper returned "mount: according to mtab, unionfs is already mounted on / 
mount failed". I have no idea why it's suddenly called unionfs.

**ETA3:** Went into mtab and fstab both and changed unionfs to /dev/hda1. Apparently no change. Can't unmount /dev/hda1 via GPE, if try get the error that device is busy.

**ETA4:** Used GPE to set Device --> Disklabel, and it says it wiped all partitions and rewrote /dev/hda1 as the primary partition with a size of 11.24GB, but Filesystem still says it only has 13.2 MB free. Fstab now lists "hda1 / hda1 rw 0 0 " first, and mtab lists "/dev/hda1 / ext3 rw 0 0" first; unionfs isn't on either of them any more. Using GPE to check the Info for hda1 has the Warning tag: "Unable to detect filsystem! Possible reasons are:
-The filesystem is damaged
-The filesystem is unknown to libparted
-There is no filesystem available (unformatted)"

**ETA5:** Running mount in terminal returned:
"/dev/hda1 on / type ext3 (rw)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)"

---

### Post by Halfling Rogue on 2007-06-11
Checked "mount" on my functional laptop that already has Dapper installed; the only two different lines were the first and last, which returned as:
"/dev/hda1 on / type ext3 (rw,errors=remount-ro)"
"binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)"

Not sure how to change hda1 to "errors=remount-ro".

**ETA:** Tried editing it directly in mtab and fstab, no change. Rebooting.

---

