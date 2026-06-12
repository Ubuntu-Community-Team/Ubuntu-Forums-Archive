---
title: "apt-get failing on update"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by rowlando on 2006-12-16
When I tried to running an update I get the error messages below. I think it could be because I switched user whilst I was running an update. How can I recover from this?

```
nick@ubuntu:~$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-image-2.6.17-10-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/23.0MB of archives.
After unpacking 844kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 113082 files and directories currently installed.)
Preparing to replace linux-image-2.6.17-10-generic 2.6.17-10.33 (using .../linux-image-2.6.17-10-generic_2.6.17.1-10.34_i386.deb) ...
The directory /lib/modules/2.6.17-10-generic still exists. Continuing as directed.
Done.
Unpacking replacement linux-image-2.6.17-10-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.17-10-generic_2.6.17.1-10.34_i386.deb (--unpack):
 unable to create `./boot/config-2.6.17-10-generic': Read-only file system
Running postrm hook /sbin/update-grub .
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
cp: cannot create regular file `/boot/grub/menu.lst~': Read-only file system
User hook script /sbin/update-grub failed at /var/lib/dpkg/tmp.ci/postrm line 288.
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.17-10-generic_2.6.17.1-10.34_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
nick@ubuntu:~$
```

---

### Post by Kobalt on 2006-12-16
Have you tried running Synaptic and selecting "repair broken packages" ?

---

### Post by rowlando on 2006-12-16
I hadn't. I've just tried now but according to Synaptic, no packages are broken.

What's the next step I can try?

---

### Post by hal10000 on 2006-12-16
Please post the output of the command [COLOR="Red"]mount[/COLOR] and the content of your /etc/fstab file.
It seems that your /boot partition (or directory) resides in a read-only filesystem. That's the reason why the install-process can't create files in this directory.

---

### Post by rowlando on 2006-12-16
Here's the output of mount:
```
nick@ubuntu:~$ mount
/dev/.static/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/hda1 on /boot type ext2 (ro)
/dev/hda4 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1001,gid=1001,umask=077,iocharset=utf8)

```

and here's the contents of /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=fc3581f1-43e6-441f-bfc5-800c6c0b9c7f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=3babd9c1-3568-4fb8-b0fd-13797c0b9d7f /boot           ext2    ro              0       2
# /dev/hda4
UUID=fb58fdec-4335-4d2d-b242-f54a7b8fc2b6 /home           ext3    defaults        0       2
# /dev/hda2
UUID=9a4f24f4-6741-4f00-879f-62002dc48dd2 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by hal10000 on 2006-12-16
The decisive row in your /etc/fstab file is:
```
UUID=3babd9c1-3568-4fb8-b0fd-13797c0b9d7f /boot           ext2    ro              0       2
```
Change it to ```
UUID=3babd9c1-3568-4fb8-b0fd-13797c0b9d7f /boot           ext2    defaults              0       2
```
and everything shold work.
You have to edit the fstab file with root-permissions, so try [COLOR="Red"]sudo gedit /etc/fstab[/COLOR], or instead of gedit any other texteditor you like. If you don't like to reboot, then you can just do: [COLOR="Red"]sudo mount /boot -o remount,rw[/COLOR].

---

### Post by rowlando on 2006-12-16
Fantastic. Thanks for that.

---

