---
title: "[SOLVED] &amp;quot;linux-image&amp;quot; and &amp;quot;linux-ubuntu-modules&amp;quot; Dependency Problems"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Okuryo on 2008-01-02
Ever since I've upgraded to Gutsy, I've been having dependency problems with the *linux-ubuntu-modules-2.6.22-14-386* and *linux-image-2.6.22-14-386* packages.

Whenever I install or remove a package with *apt-get,* *aptitude* or *Synaptic*, it says I have dependency problems with them and it can't fix them.

Recently I downloaded the .deb for the packages' Hardy versions [2.6.24-2] to see if it helps, but it just got worse. Now when I try to do anything with *aptitude*, I get an output of this fashion:

```
The following packages are BROKEN:
  linux-ubuntu-modules-2.6.22-14-386 linux-ubuntu-modules-2.6.24-2-386 
The following packages have been kept back:
  tzdata wine 
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/3051kB of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  linux-ubuntu-modules-2.6.24-2-386: Depends: linux-image-2.6.24-2-386 but it is not installable
  linux-ubuntu-modules-2.6.22-14-386: Depends: linux-image-2.6.22-14-386 but it is not installable
Resolving dependencies...
E: I wasn't able to locate file for the linux-ubuntu-modules-2.6.24-2-386 package. This might mean you need to manually fix this package.
The following actions will resolve these dependencies:

Remove the following packages:
linux-ubuntu-modules-2.6.24-2-386

Install the following packages:
grub [0.97-29ubuntu4 (gutsy)]
linux-image-2.6.22-14-386 [2.6.22-14.47 (gutsy-updates, gutsy-security)]

Score is 101

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  grub linux-image-2.6.22-14-386 
The following packages will be automatically REMOVED:
  linux-ubuntu-modules-2.6.24-2-386 
The following packages have been kept back:
  tzdata wine 
The following NEW packages will be installed:
  grub linux-image-2.6.22-14-386 
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-2-386 
0 packages upgraded, 2 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B/22.0MB of archives. After unpacking 55.2MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 220296 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-2-386 ...
FATAL: Could not open '/boot/System.map-2.6.24-2-386': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-2-386
find: /lib/firmware/2.6.22-14-generic: No such file or directory
find: /lib/firmware/2.6.22-14-generic: No such file or directory
find: /lib/firmware/2.6.22-14-generic: No such file or directory
find: /lib/firmware/2.6.22-14-generic: No such file or directory
find: /lib/firmware/2.6.22-14-generic: No such file or directory
find: /lib/firmware/2.6.22-14-generic: No such file or directory
Adding binary /usr/share/initramfs-tools/init
Adding binary /etc/initramfs-tools/initramfs.conf
Adding binary /etc/initramfs-tools/conf.d/resume
Adding binary /usr/lib/initramfs-tools/bin//busybox
Adding binary /sbin/modprobe
Adding library /lib/libc.so.6
Adding library /lib/ld-linux.so.2
Adding binary /sbin/depmod
Adding binary /sbin/rmmod
Calling hook apparmor
Calling hook brltty
Adding binary /usr/share/brltty/initramfs/brltty.sh
Adding binary /sbin/brltty-setup
Calling hook fuse_utils
Adding binary /sbin/mount.fuse
Calling hook kernelextras
Calling hook ntfs_3g
Adding binary /bin/ntfs-3g
Adding library /lib/libntfs-3g.so.12
Adding library /lib/libfuse.so.2
Adding library /lib/libdl.so.2
Adding library /lib/librt.so.1
Adding library /lib/libpthread.so.0
Calling hook thermal
Calling hook udev
Adding binary /usr/bin/pkill
Adding library /lib/libproc-3.2.7.so
Adding binary /sbin/udevd
Adding library /lib/libselinux.so.1
Adding library /lib/libsepol.so.1
Adding binary /sbin/udevtrigger
Adding binary /sbin/udevsettle
Adding binary /lib/udev/dvb_device_name
Adding binary /lib/udev/usb_device_name
Adding binary /lib/udev/ata_id
Adding binary /lib/udev/edd_id
Adding binary /lib/udev/usb_id
Adding binary /lib/udev/vol_id
Adding library /lib/libvolume_id.so.0
Adding binary /lib/udev/scsi_id
Adding binary /lib/udev/path_id
Adding binary /lib/udev/firmware_helper
Adding binary /lib/udev/pnp_modules
Adding binary /lib/udev/ide_media
Adding binary /lib/udev/vio_type
Adding binary /lib/udev/watershed
Calling hook usplash
Adding binary /sbin/usplash
Adding library /lib/libusplash.so.0
Adding library /lib/libx86.so.1
Adding binary /sbin/usplash_write
Adding binary /etc/usplash.conf
Adding binary /usr/lib/usplash/usplash-artwork.so
Calling hook console_tools
Adding binary /usr/bin/consolechars
Adding library /lib/libconsole.so.0
Adding library /lib/libcfont.so.0
Adding library /lib/libctutils.so.0
Adding binary /bin/kbd_mode
Adding binary /bin/loadkeys
Calling hook dmsetup
Adding binary /sbin/dmsetup
Adding library /lib/libdevmapper.so.1.02.1
Calling hook console_setup
Building cpio /boot/initrd.img-2.6.22-14-generic initramfs
Working files in /tmp/mkinitramfs_b28043 and overlay in /tmp/mkinitramfs-OL_Y28044
sha1sum: /boot/initrd.img-2.6.24-2-386: No such file or directory
dpkg: error processing linux-ubuntu-modules-2.6.24-2-386 (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-2-386
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done

```

Please help, I'm honestly clueless.

[I haven't restarted yet since I attempted my little experiment, and I'm not sure it's going to boot successfully if I do...]

---

### Post by overdrank on 2008-01-02
HI and I was able to install both on Gutsy, have you enabled all your repos. You can use this command ```
gksudo gedit /etc/apt/sources.list
```
Example
```
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
```
You can remove the # in front of the repos you wish to add. And don't forget to update first. Hope this helps and good luck!

---

### Post by Okuryo on 2008-01-02
Thanks, but nothing worked. I decided on just reinstalling Gutsy fresh, So no problems anymore :)

---

