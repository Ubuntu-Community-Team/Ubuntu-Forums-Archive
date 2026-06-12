---
title: "Ipod will not Mount"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by rdavis7408 on 2007-04-16
My 3rd generation ipod will no longer auto mount. I have searched and attempted to mount manually but do not know how to tell what device the ipod is called. For example I have tried the following with no success:

sudo mount  /dev/sda2 /mnt/ipod vfat
sudo mount /dev/sda /mnt/ipod vfat
sudo mount /dev/sdc /mnt/ipod vfat
sudo mount /dev/sda2 /media/ipod vfat
sudo mount /dev/sda /media/ipod vfat

When I go to the following:

sudo gedit /etc/fstab

And add the following at the bottom of the file:

/dev/sdc2 /media/iPod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0

I can then see it in the file system in Computer but am unable to mount it.

I get a error: mount: special device /dev/sdc does not exist

I am connecting using a fire wire. 

The following is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=47ecd00e-7b06-4e59-9d91-e9056f3be3b0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=a27e3198-9895-486b-a57c-0c338d939354 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdc /media/ipod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0

The following is my mtab file:

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-11-386/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
_/dev/hda1 /mnt/ipod ext3 rw 0 0_

I do not know that the final line in the mtab file has always been there, I may have added it when trying to fix the problem. Because the device hda1 appears in the first line also.

I really could use any ideas on this issue. Thanks ahead of time.

---

### Post by finer recliner on 2007-04-17
looks like you give your ipod "noauto" in your fstab which im guessing is to disable the automount feature for this device.


also you say you added the line
/dev/sdc2 /media/iPod vfat.... 
to your fstab, but it doesnt match the full fstab file you included. maybe there's a typo (sdc vs. sdc2)

---

### Post by rdavis7408 on 2007-04-17
I tried the fixes of removing the noauto from the fstab and tried to mount the drive with no success.

The following is where I attempted to mount the drive:

rdavis@rdavis-desktop:~$ sudo mount /dev/sdc /media/ipod
mount: special device /dev/sdc does not exist
rdavis@rdavis-desktop:~$ sudo mount /dev/sdc /mnt/ipod
mount: special device /dev/sdc does not exist
rdavis@rdavis-desktop:~$ sudo mount /dev/sdc /mnt/ipod
mount: special device /dev/sdc does not exist
rdavis@rdavis-desktop:~$ sudo mount /dev/sdc /mnt/ipod
mount: special device /dev/sdc does not exist
rdavis@rdavis-desktop:~$ sudo mount /dev/sdc2 /mnt/ipod
mount: special device /dev/sdc2 does not exist
rdavis@rdavis-desktop:~$ sudo mount /dev/sdc2 /media/ipod
mount: special device /dev/sdc2 does not exist
rdavis@rdavis-desktop:~$ sudo mount /dev/sdc /media/ipod
mount: special device /dev/sdc does not exist

I keep getting "mount: special device /dev/sdc does not exist" errors. Any ideas

---

### Post by kordite on 2007-05-13
I have run into a similar problem. I had Ubuntu v6.06 installed and my iPod would mount just fine. No setting changes, just plug and play. Since upgrading to v7.04, nothing.

---

### Post by kordite on 2007-06-04
I have solved my problem by connecting the external power supply to my USB hub. Apparently Ubuntu v6 is able to see the iPod with the onboard power but v7 needs more power to recognize that the USB device is even plugged in.

---

