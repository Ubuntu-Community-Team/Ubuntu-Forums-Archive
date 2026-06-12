---
title: "Can't Access New ext3 partition"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by CptnFantasy on 2007-12-27
I resized a 300 gig ntfs partition to 280 gigs using the gnome partition editor and formated those other twenty gigs to ext3. That when things started to get strange. When i attempt to access the new partition I am prompted to give the root password for security reasons...???also I have no read/write abilities.  the fstab looks like this:
proc /proc proc defaults 0 0
# Entry for /dev/hda6 :
UUID=686f0f39-d8ee-4d4d-8ec7-55bd917c3f3a / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda1 :
UUID=FC306AD1306A9306 /media/hda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hda5 :
UUID=9E90923F90921DB9 /media/hda5 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hdb1 :
UUID=067CE63E7CE627DF /media/hdb1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hda7 :
UUID=045662b0-3fba-4150-8b22-eaf343365b41 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0

hmmm I don't seem to see the new partition in there... its mounted as /media/disk-1
I'm scared.
please help.

---

### Post by taurus on 2007-12-27
Can you post

```
sudo fdisk -l
mount
```

If it's ext3, you just have to change the ownership of that mount point from root to your login name so you can write to it.

---

### Post by CptnFantasy on 2007-12-27
the terminal told me this:
sudo: fdisk: command not found
???
I do not understand

---

### Post by kshane on 2007-12-27
> **CptnFantasy said:**
> the terminal told me this:
sudo: fdisk: command not found
???
I do not understand

Please post the screen output from this...

```
sudo fdisk -l
```

---

### Post by CptnFantasy on 2007-12-27
poopie@poopie:~$ sudo fdisk -l
[sudo] password for poopie:
sudo: fdisk: command not found
poopie@poopie:~$ 

did I not enter the command correctly?

---

### Post by lgambett on 2007-12-27
There is a space between fdisk and -l...

---

### Post by CptnFantasy on 2007-12-27
yeah thats how I entered it...still got the same thing:

poopie@poopie:~$ sudo fdisk -l
sudo: fdisk: command not found
poopie@poopie:~$ 

I am running 7.10 64bit if that is of any consequence.

---

### Post by xeth_delta on 2007-12-27
> **CptnFantasy said:**
> yeah thats how I entered it...still got the same thing:

poopie@poopie:~$ sudo fdisk -l
sudo: fdisk: command not found
poopie@poopie:~$ 

I am running 7.10 64bit if that is of any consequence.

What is the output of "find /sbin/* | grep -i fdisk"?

---

### Post by CptnFantasy on 2007-12-27
this:
poopie@poopie:~$ find /sbin/*
/sbin/acpi_available
/sbin/alsactl
/sbin/apm_available
/sbin/apparmor_parser
/sbin/badblocks
/sbin/blkid
/sbin/brltty
/sbin/brltty-config
/sbin/brltty-setup
/sbin/debugfs
/sbin/debugreiserfs
/sbin/depmod
/sbin/dhclient
/sbin/dhclient3
/sbin/dhclient-script
/sbin/discover
/sbin/dosfsck
/sbin/dumpe2fs
/sbin/e2fsck
/sbin/e2image
/sbin/e2label
/sbin/findfs
/sbin/fsck
/sbin/fsck.ext2
/sbin/fsck.ext3
/sbin/fsck.msdos
/sbin/fsck.nfs
/sbin/fsck.reiserfs
/sbin/fsck.vfat
/sbin/grub-install
/sbin/halt
/sbin/hdparm
/sbin/ifconfig
/sbin/ifdown
/sbin/ifup
/sbin/init
/sbin/initctl
/sbin/insmod
/sbin/installkernel
/sbin/ip
/sbin/ip6tables
/sbin/ip6tables-restore
/sbin/ip6tables-save
/sbin/ipmaddr
/sbin/iptables
/sbin/iptables-restore
/sbin/iptables-save
/sbin/iptunnel
/sbin/ipw3945d-2.6.22-14-rt
/sbin/iwconfig
/sbin/iwevent
/sbin/iwgetid
/sbin/iwlist
/sbin/iwpriv
/sbin/iwspy
/sbin/kallsyms
/sbin/kbdrate
/sbin/killall5
/sbin/klogd
/sbin/ksyms
/sbin/ldconfig
/sbin/ldconfig.real
/sbin/logd
/sbin/logsave
/sbin/losetup
/sbin/lrm-manager
/sbin/lrm-video
/sbin/lsmod
/sbin/lsmod.modutils
/sbin/lspcmcia
/sbin/MAKEDEV
/sbin/mii-tool
/sbin/mkdosfs
/sbin/mke2fs
/sbin/mkfs.ext2
/sbin/mkfs.ext3
/sbin/mkfs.msdos
/sbin/mkfs.reiserfs
/sbin/mkfs.vfat
/sbin/mkreiserfs
/sbin/modinfo
/sbin/modprobe
/sbin/modprobe.modutils
/sbin/mount.fuse
/sbin/mount.ntfs
/sbin/mount.ntfs-3g
/sbin/nameif
/sbin/netbug
/sbin/on_ac_power
/sbin/pam_tally
/sbin/parted
/sbin/partprobe
/sbin/pccardctl
/sbin/plipconfig
/sbin/poweroff
/sbin/rarp
/sbin/readahead-list
/sbin/readahead-watch
/sbin/reboot
/sbin/reiserfsck
/sbin/reiserfstune
/sbin/resize2fs
/sbin/resize_reiserfs
/sbin/rmmod
/sbin/rmmod.modutils
/sbin/route
/sbin/rtacct
/sbin/rtmon
/sbin/runlevel
/sbin/shadowconfig
/sbin/shutdown
/sbin/slattach
/sbin/ss
/sbin/start
/sbin/start-stop-daemon
/sbin/status
/sbin/stop
/sbin/sulogin
/sbin/swapoff
/sbin/swapon
/sbin/sysctl
/sbin/syslogd
/sbin/tc
/sbin/telinit
/sbin/tune2fs
/sbin/udevcontrol
/sbin/udevd
/sbin/udevmonitor
/sbin/udevsettle
/sbin/udevtrigger
/sbin/unix_chkpwd
/sbin/update-grub
/sbin/update-modules
/sbin/usplash
/sbin/usplash_down
/sbin/usplash_write
/sbin/vol_id
/sbin/wpa_action
/sbin/wpa_cli
/sbin/wpa_supplicant
poopie@poopie:~$ grep -i fdisk

poopie@poopie:~$

---

### Post by taurus on 2007-12-27
Do you have gparted installed on your machine, System -> Administration?  If you don't, install it.  Then, run it and post the screen shots of your drives, /dev/hda & /dev/hdb.

p.s.  Did you use the LiveCD or the alternate CD (or the server CD)?

---

### Post by xeth_delta on 2007-12-27
CptnFantasy, it seems you don't have the fdisk executable. By the way, the complete command I mentioned was:
```
find /sbin/* | grep -i fdisk
```
It searches through /sbin, filtering the output lines that contain the word fdisk :)

---

### Post by CptnFantasy on 2007-12-27
First: I used the text based installer with the ubuntu studio distribution gutsy...
the ext3 partion shown in the second screenshot is the one dealing me grief.  here are the screen shots:

---

### Post by CptnFantasy on 2007-12-27
xeth_delta, that command does nothing:
poopie@poopie:~$ find /sbin/* | grep -i fdisk
poopie@poopie:~$

---

### Post by xeth_delta on 2007-12-27
> **CptnFantasy said:**
> xeth_delta, that command does nothing:
poopie@poopie:~$ find /sbin/* | grep -i fdisk
poopie@poopie:~$

It actually does. You don't get any output because there is no line containing fdisk. You can try, if you want, filtering for some other command you know will be in /sbin. You will see some output.

---

### Post by taurus on 2007-12-27
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb2   /media/hdb2   ext3   defaults   0   1
```
Save it and close the gedit window.  Now, create a new mount point and mount it.

```
sudo mkdir /media/hdb2
sudo umount /media/disk-1
sudo mount -a
df -h
```
And I assume you want to write to it without using sudo/gksudo.  You just have to change the ownership of /media/hdb2 from root to your login name, poopie.

```
sudo chown -R poopie:poopie /media/hdb2
```

---

### Post by CptnFantasy on 2007-12-27
Tanks alot, that worked perfectly! and I think I grasped what those commands did, I just never would have been able to do it by myself. you should become an admin or something...wait...oh. Thanks though!

---

