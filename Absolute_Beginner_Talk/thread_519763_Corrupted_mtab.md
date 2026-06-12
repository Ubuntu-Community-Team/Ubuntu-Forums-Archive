---
title: "Corrupted mtab"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Aya Dream on 2007-08-07
Noob who's been at it all day trying to install Edgy Eft on on a 4GB USB pendrive. It's up and working-ish.

Just about everything I read told me to use apt-get for this or that package but I don't have internet connection yet. Also haven't been able to network the ubuntu pendrive to the windows desktop or the windows laptop. Thus i'm left with using the laptop to access the internet and download the packages, copy them to another usb stick which I then mount in ubuntu and install with dpkg -i

What with all the rebooting of the Ubuntu pendrive and the swapping over of the USB stick with the downloaded packages, they've all been mounted and un-mounted about 20 times today! Somewhere my fstab and mtab files have got screwed up. 

In fact my mtab file turned into a directory!!!

Question: I deleted the mtab directory and rebooted so now I have an empty mtab file again. The pendrive mounts okay but the other two USB sticks although mounted do not show up on the desktop (despite preferences being set to mount on hot plug, when inserted and open browser etc)

fstab shows 2 lines:

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

sudo fdisk -l shows sda1, sdb1 (the two SATA NTFS data/backup drives), hda1, hdb1 (the two PATA NTFS WinXP drives), sdc1, sdc2 (the two pendrive partitions for Ubuntu), sdd1, sde1 (the two USB sticks with all the downloaded packages on)

mtab is now an empty blank file.

Do I have a serious problem here? How do I clear up my fstab and mtab files? Is there a re-config I can do or something?

Thanks for any help
AD

---

### Post by milosz.galazka on 2007-08-07
Hi, to recreate mtab try command:
sudo cat /proc/mounts > /etc/mtab

---

### Post by Aya Dream on 2007-08-07
Milosz, thanks for quixk and useful reply. mtab is now populated with lots of details about USB drives great!

A couple of questions:fa) fstab still looks pathetically empty i.e. still the same as reported above and b) mtab doesn't refer to any of my hard disks (hda1, hdb1, sda1 & sdb1). Is that normal Is everything ok now??

fstab:

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

mtab:

rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
/dev/sdc1 /cdrom vfat rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1 0 0
/dev/loop0 /rofs squashfs ro 0 0
/dev/sdc2 /cow ext2 rw 0 0
unionfs / unionfs rw,dirs=/cow=rw:/rofs=ro,debug=0,delete=whiteout,copyup=preserve 0 0
unionfs /dev/.static/dev unionfs rw,dirs=/cow=rw:/rofs=ro,debug=0,delete=whiteout,copyup=preserve 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.17-10-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
usbfs /dev/bus/usb/.usbfs usbfs rw 0 0
udev /proc/bus/usb tmpfs rw 0 0
usbfs /proc/bus/usb/.usbfs usbfs rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
/dev/sdd /media/usbdisk vfat rw,nosuid,nodev,uid=999,gid=999,fmask=0077,dmask=0077,codepage=cp437,iocharset=utf8,shortname=mixed,quiet 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sdf1 /media/Kingston vfat rw,nosuid,nodev,uid=999,gid=999,fmask=0077,dmask=0077,codepage=cp437,iocharset=utf8,shortname=mixed,quiet 0 0

---

