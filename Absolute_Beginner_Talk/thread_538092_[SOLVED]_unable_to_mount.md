---
title: "[SOLVED] unable to mount"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by duruttye on 2007-08-29
Hi guys!

I'm unable to mount my newly formatted drive.

kucko@kucko-mashina:~$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5005    40202631    5  Extended
/dev/sda5               1        5005    40202599+  83  Linux

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4787    38451546   83  Linux
/dev/sdb2            4788        4998     1694857+   5  Extended
/dev/sdb5            4788        4998     1694826   82  Linux swap / Solaris

The drive in question is the first one. This is what I get.

kucko@kucko-mashina:~$ mount /dev/sda
mount: can't find /dev/sda in /etc/fstab or /etc/mtab
kucko@kucko-mashina:~$ mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
kucko@kucko-mashina:~$ mount /dev/sda5

The content of /etc/fstab

# /dev/sda1
UUID=23665c3c-a0b4-4633-90d2-0aa0a5783f40 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=83a33931-ac90-4c2f-a6a2-6aa03c7f144d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Any suggestions?

---

### Post by kellemes on 2007-08-29
from commandline you need to first create a dir like so..

```
mkdir /media/mydisk
mount /dev/sda5 /media/mydisk
```

Obviously you have to tweak permissions and such..

---

### Post by duruttye on 2007-08-29
Ok, that was fast. Thanx

Already changed the ownership, will that be there after reboot too?

Or I will have to do that every time?

---

### Post by glotz on 2007-08-29
The folder you made /media/mydisk will be there. The disk won't be mounted however, unless you add it to fstab.

---

### Post by Inxsible on 2007-08-29
if its an external drive, you should use pmount. pmount mounts the drive under /media and it always automounts. If its an internal, then fstab is the best bet :)

To automount an internal drive, add the "auto" option to the drive entry in fstab

---

### Post by duruttye on 2007-08-29
I could really use some help in doing that :)

---

### Post by duruttye on 2007-08-29
It's not an external drive, it's a normal hard drive... I think

---

### Post by Inxsible on 2007-08-29
> **duruttye said:**
> It's not an external drive, it's a normal hard drive... I thinkby normal i think you mean internal :D.

I know you have posted your fdisk earlier, could you tell me what drive you want to auto mount so i can give you a command?

is it sda5 and where is it mounted /media/mydisk or some other folder that you created ??

---

### Post by duruttye on 2007-08-29
Internal yesssss, 'cause it's IN the box :)

Right now sda5 is mounted in /media/mydisk, and this is my precious drive that wouldn't mount.

---

### Post by Zalbor on 2007-08-29
Guys... It's very simple what the problem is! fstab mounts partitions based on UUID, if the drive was formatted then the UUID changed!
Try this command:
```
ls -l /dev/disk/by-uuid/
```
and it will show the corresponding UUID for each drive. Find the one for sda1, and replace the UUID in fstab with the new one.

---

### Post by duruttye on 2007-08-29
There is no sda...

kucko@kucko-mashina:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2007-08-29 08:31 23665c3c-a0b4-4633-90d2-0aa0a5783f40 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-08-29 08:31 83a33931-ac90-4c2f-a6a2-6aa03c7f144d -> ../../sdb5


And that's it.

---

### Post by Zalbor on 2007-08-29
Sorry, I probably should have paid better attention. I thought it was a second drive you reformatted. :|

So it's the main one, you formatted it, then reinstalled Ubuntu and it's not working? I'm confused...

---

### Post by Inxsible on 2007-08-29
> **duruttye said:**
> Internal yesssss, 'cause it's IN the box :)

Right now sda5 is mounted in /media/mydisk, and this is my precious drive that wouldn't mount.If you do not have an entry for sda5 in fstab at all, then add this line

```
/dev/sda5 /media/mydisk ext3 defaults, 0 2
```If you already have one, then make it look like this one

---

### Post by duruttye on 2007-08-29
That was the xp drive... and there's the reason. Ubuntu was on the slave drive. After the formatting, I couldn't mount it.

---

### Post by Inxsible on 2007-08-29
> **duruttye said:**
> That was the xp drive... and there's the reason. Ubuntu was on the slave drive. After the formatting, I couldn't mount it.

so you are saying sda5 is an XP = NTFS drive ? but your fdisk on the first post says sda5 is Linux drive.

Now I am confused !!!

---

### Post by duruttye on 2007-08-29
> **Inxsible said:**
> If you do not have an entry for sda5 in fstab at all, then add this line

```
/dev/sda5 /media/mydisk ext3 defaults, 0 2
```If you already have one, then make it look like this one

Ok, added it. This means, that after reboot it will be there? Or I will have to do this every time?

---

### Post by duruttye on 2007-08-29
> **Inxsible said:**
> so you are saying sda5 is an XP = NTFS drive ? but your fdisk on the first post says sda5 is Linux drive.

Now I am confused !!!

I'm confused too:)
I formatted it a few times, but not in ntfs.

---

### Post by bogolisk on 2007-08-29
> **duruttye said:**
> 

Any suggestions?

first please do
```

mount

```

so we can see what is currently mount. In general you don't mount the disk (/dev/sda) but you should mount the partitions on the disk (/dev/sda1, /dev/sda5, etc.)

---

### Post by duruttye on 2007-08-29
Here you go:

kucko@kucko-mashina:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda5 on /media/mydisk type ext3 (rw)

---

### Post by bogolisk on 2007-08-29
[QUOTE=duruttye;3276239]Here you go:
I think everything is fine excepts for the "misleading" comments in for /etc/fstab

[list]
[*] /dev/sdb1 is your root filesystem
[*] /dev/sdb5 is your swap
[*] /dev/sda5 is your newly formated disk
[*] the reason why /dev/sda5 was NOT in /dev/disk/by-uuid/ is udev was not restarted. So next reboot it will be there or do a
```

sudo /etc/init.d/udev retart

```
[*] for a non-removable discs you'll have to add its entry in /etc/fstab which you did. so it's fine and dandy.
[/list]

Just one thing: **Are you sure that next time you boot, that the box won't try to boot from /dev/sda even if your root fileystem is on /dev/sdb?**

---

### Post by duruttye on 2007-08-29
You're right, after reboot, the drive is mounted.
Problem solved!
Thank you for your support!!!

---

### Post by Inxsible on 2007-08-29
> **duruttye said:**
> You're right, after reboot, the drive is mounted.
Problem solved!
Thank you for your support!!!
Mark your thread solved :)

Top right corner Thread Tools --> Mark Thread As Solved.  :popcorn:

---

