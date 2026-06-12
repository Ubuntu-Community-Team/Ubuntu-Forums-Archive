---
title: "Dual Boot With Mac OS X &amp; Ubuntu 6.06.1"
date: 2006-09-15
forum: Apple PPC Users
---

### Post by sbentzen on 2006-09-15
i downloaded the live cd, booted it up and tried to install but the disk partition table editor seems really difficult and seems like it would end up destroying my os partition, what do i do. using ppc ibook G4:confused:

---

### Post by linear on 2006-09-16
If the partition editor scares you, you may want to go the backup, partition, reinstall OS X, install Ubuntu route. You may also need to use the alternate installer. The Desktop CD installer fails on some G4 systems.

For starters, read these:

_[https://help.ubuntu.com/community/Installation/PowerPC](https://help.ubuntu.com/community/Installation/PowerPC) _(for Breezy, but still helpful)
[http://www.askdavetaylor.com/how_do_..._mac_os_x.html]("http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html")

This worked for me:

0. Read up in the PPC forum on any model specific quirks.
1. If you need to save the OS X partition, back it up. ([Carbon Copy Cloner]("http://www.bombich.com/software/ccc.html") works well.)
2. Repartition disk. Make two partitions, leave first as free space and second for OS X. Disk Utility is destructive (another reason for the back up), or there is a howto [here]("http://ubuntuforums.org/showthread.php?t=89960") on using **parted** to resize non-destructively.
3. Boot from the Ubuntu install disk. When you get to the partitioning step, tell the installer to use the largest free space. It will take care of the rest.

---

### Post by sbentzen on 2006-09-16
thank you for the reply though i would like to keep my os partition because the person in control would be pissed, though do you think i would be able to boot off the installer cd then partition the drive?

---

### Post by linear on 2006-09-16
People have reported success with the [parted]("http://ubuntuforums.org/showthread.php?t=89960") method, but I haven't tried it myself.

Keep in mind that the "person in control" will be even more pissed if you hose the disk. A backup is strongly recommended.

---

### Post by sbentzen on 2006-09-17
thankyou and i also do have a backup though, i must say i am quite scared of the command line, (fear of making a one byte mistake and overwriting data)

---

### Post by AlphaMack on 2006-09-20
If you have a total backup of OS X, use Disk Utility on the OS X installation CD.  Create 2 or 3 partitions depending on whether you want to use a shared partition between the two.

First partition = OS X.  Mark as HFS+ (journaled).
Second partition = Ubuntu.  Mark as FREE SPACE.
Third partition (optional) = shared.  Mark as HFS+ (no journaling).

1.  Install OS X on your partition made for OS X.
2.  Using the Ubuntu CD, go through the installation.  When you get to the partition editor, have Ubuntu automatically partition the free space.  You'll get your /boot, /, and /swap created for you.
3.  If you have a third partition, edit your /etc/fstab.  Create a folder in /mnt to represent your mount point.  Then in your fstab:

```
/dev/hdaX /mnt/nameofyourfolder hfsplus defaults 0 0
```

where X is a number corresponding to your partition (e.g. /dev/hda5) and 'nameofyourfolder' is the name of your partition.  Once you edit your fstab, go to System->Administration->Disks, locate your shared partition and enable it.  That's it.

Now you can go back and transfer your OS X stuff back over when you boot into OS X.

If you prefer, you can have a separate partition for your /home, but I recommend doing that through the alternate CD installer.

---

### Post by sbentzen on 2006-09-20
why does it look as if i must totally wipe my hard drive? i don't want to do that.

---

