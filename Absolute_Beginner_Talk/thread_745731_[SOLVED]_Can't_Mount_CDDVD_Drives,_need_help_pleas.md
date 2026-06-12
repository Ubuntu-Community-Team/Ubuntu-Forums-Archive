---
title: "[SOLVED] Can't Mount CD/DVD Drives, need help please..."
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by fparedesg on 2008-04-04
I'm having some problems with my DVD and CD drives. I can't mount the drives, and I can't use them.The DVD is the master, and the CD is the slave. My computer has Windows Vista, and Ubuntu 7.10. The only problem is that my Internet connection is not working yet, and I need to use an installation CD to be able to use it, and I can't do that if the CD drive is not mounted.

This is what I put on the terminal and what I got:
```
federico@tiburon:~$ sudo mount -t udf /dev/scd0 /media/cdrom0/
mount: special device /dev/scd0 does not exist
```
When I check in the /dev folder, there is no scd0 file.

So I put:
```
sudo gedit /etc/fstab
```
This is what I got on the last three lines:
```
UUID=e081e30a-cae5-412b-8f40-dda7ddd868ec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
```

Please, if you can help me, thank you very much..

---

### Post by herbster on 2008-04-04
```
cat /proc/devices
```

Paste output.

---

### Post by fparedesg on 2008-04-05
Thank you for helping, sorry it took so long, this is what I got:
```
federico@tiburon:~$ cat /proc/devices
Charecter devices:
  1 mem
  2 pty
  3 ttyp
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  6 lp
  7 vcs
 10 misc
 13 input
 14 sound
 21 sg
 29 fb
 99 ppdev
116 alsa
128 ptm
136 pts
171 ieee1394
180 usb
189 usb_device
216 rfcomm
226 drm
253 heci
254 usb_endpoint

Block devices:
  1 ramdisk
  8 sd
 65 sd
 66 sd
 67 sd
 68 sd
 69 sd
 70 sd
 71 sd
128 sd
129 sd
130 sd
131 sd
132 sd
133 sd
134 sd
135 sd
```

---

### Post by herbster on 2008-04-05
Oops, please paste the output of this instead:

```
cat /proc/sys/dev/cdrom/info
```

---

### Post by fparedesg on 2008-04-05
Ok, this is what I got:
```
federico@tiburon:~$ cat /proc/sys/dev/cdrom/info
cat: /proc/sys/dev/cdrom/info: No such file or directory
```
I checked in the dev folder, there is no cdrom folder.

---

### Post by herbster on 2008-04-05
Sorry, we're using different distros so I'm going by what works for me. What do you have in the dev folder?

---

### Post by fparedesg on 2008-04-05
I have "hpet", "mac_hid", "parport", "rtc", "scsi"

---

### Post by herbster on 2008-04-06
Paste what you get from "cat /proc/"

---

### Post by fparedesg on 2008-04-06
It says:
```
federico@tiburon:~$ cat /proc/
cat: /proc/ Is a directory
```

---

### Post by Michael.Godawski on 2008-04-06
Please post the results of:

```
sudo lshw -C disk
mount
```

---

### Post by fparedesg on 2008-04-06
```
federico@tiburon:~$ sudo lshw -C disk
[sudo] password for federico:
  *-disk                  
       description: SCSI Disk
       product: WDC WD2000JD-00G
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 02.0
       serial: WD-WMAEP3329441
       size: 186GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
federico@tiburon:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda3 on /media/sda3 type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
federico@tiburon:~$
```

---

### Post by herbster on 2008-04-06
Try "cat /proc/sys/dev/cdrom/info"

---

### Post by fparedesg on 2008-04-06
```
federico@tiburon:~$ cat /proc/sys/dev/cdrom/info
cat: /proc/sys/dev/cdrom/info: No such file or directory 
```

---

### Post by herbster on 2008-04-06
Crap, my bad I already tried that in the first page, sorry.

Okay, have you checked your connection with the physical drive? Do you have Windows also installed on your computer and therefore can check to see that it indeed works? I'm assuming you installed off a LiveCD, so it must, right? Just double-checking.

Do

```
cd /dev && ls
```

Paste that.

---

### Post by fparedesg on 2008-04-06
Crap..I never thought it would be a problem with the physical drive, considering I **did** install Ubuntu using a LiveCD, and that the CD drive did work in Windows. The CD drive did work, but the DVD drive wouldn't even open. What I did was to turn it off and disconnect both the DVD and CD drives (and remove the master/slave jumpers), then I reconnected the CD drive alone and booted Ubuntu. It worked now (and it also takes 20 seconds less to load grub, don't know why..). Sorry to have bothered you before, and thank you for helping me.

---

