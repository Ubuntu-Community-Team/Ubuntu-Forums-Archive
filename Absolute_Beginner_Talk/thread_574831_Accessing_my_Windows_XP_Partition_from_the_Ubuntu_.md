---
title: "Accessing my Windows XP Partition from the Ubuntu side"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by duckblind123 on 2007-10-13
I am really new to Ubuntu, but find it very easy to use (somewhat).  There are a
couple of items I do yet understand, but I am willing to try.  The first involves my
Windows partition.  Is it pssible to access the data from my Ubuntu side?  I have
run the sudo fdisk -lu command and find the following:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    39712679    19856308+   7  HPFS/NTFS
/dev/hda2        39712680    76662179    18474750   83  Linux
/dev/hda3        76662180    78156224      747022+   5  Extended
/dev/hda5        76662243    78156224      746991   82  Linux swap / Solaris

I also ran the mount command and found the following:
 mjdesktop@mjdesktop:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-29-386/volatile type tmpfs (rw)

Again, I am new to Ubuntu, so can someone help me make my Windows files
accessible from the Ubuntu side?
Thanks, duckblind123

---

### Post by taurus on 2007-10-13
Here's a link for you, [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G).

---

### Post by vanadium on 2007-10-13
As we are in the "absolute beginners" section, you probably will need a bit more insight in order to benefit from that link. What we see is that your Windows partition is not mounted. Yet, in a default install, a Windows volume is automatically being set up to be mounted under /media. This makes me suspect that for the moment, your Windows volume is not OK. It might have the "dirty" flag set and needs to be checked. As far as i know, a "dirty" volume is not mounted by Ubuntu.

Before moving on and following the link, exit Ubuntu and boot into Windows. Probably, your Windows volume will be checked and corrected while booting Windows. Then exit Windows, boot Ubuntu again and run the "mount" command again. It will probably be in the output now, and moreover, you probably will see the Windows volume on your Ubuntu desktop now .

The link taurus pointed to is to take it one step further. By default, Ubuntu can only read an ntfs volume, not write to it. This is because ntfs is a proprietary format by Microsoft with no specifications published. However, currently the "next generation" ntfs driver, ntfs-3g is stable, and that one allows to write to ntfs volumes. The link learns you how to install ntfs-3g, but before you do that, you must make sure your volume is correctly mounted with the standard driver. The next Ubuntu version, Gutsy, which is tobe released within two days, will by default use the ntfs-3g driver.

---

### Post by duckblind123 on 2007-10-14
RESOLVED - Thanks you for your help.  I was able to correct the problem and properly mount the drive.  Now when I boot Ubtunu, the HDA1 icon shows up on the desktop.
Thanks again, duckblind123

---

