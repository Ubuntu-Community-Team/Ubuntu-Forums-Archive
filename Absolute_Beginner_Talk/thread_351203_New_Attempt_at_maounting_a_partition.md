---
title: "New Attempt at maounting a partition"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by cmk_78212 on 2007-02-01
I am trying to view my windows xp files on my new install of 6.10.  I got my advice from:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

I think the problem is that those instructions are for those with Hard Disk.  I have two hard disks.  Drive D is partitioned as NTFS with a small FAT32 back up.  Drive E is partitioned by the graphical Ubuntu intilation between NTFS and Ubuntu.  Dive D is the main windows drive I would live to have access to.

When I do: sudo fdisk -l
I get:Disk /dev/hda: 163.9 GB, 163928604672 bytes
240 heads, 63 sectors/track, 21175 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         765     5783368+   b  W95 FAT32
/dev/hda2   *         766       21174   154292040    7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9202    73915033+   7  HPFS/NTFS
/dev/hdb2   *        9203       19038    79007670   83  Linux
/dev/hdb3           19039       19457     3365617+   5  Extended
/dev/hdb5           19039       19457     3365586   82  Linux swap / Solaris


That is where I get lost on the instructions from psychocats because it seems that their instructions are just for one drive.

Any ideas on where to take it next?

Thanks

---

### Post by taurus on 2007-02-01
Edit /etc/fstab by running

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and add the following three lines to the end of it.

```

/dev/hda1   /media/hda1   vfat   iocharset=utf8,umask=000   0   0
/dev/hda2   /media/hda2   ntfs   nls=utf8,umask=0222   0   0
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0

```
Save the chances.  Now, create the three new mount points and mount them

```
sudo mkdir /media/hda1 /media/hda2 /media/hdb1
sudo mount -a
df -h
```

---

### Post by cmk_78212 on 2007-02-01
Thanks for the help.  This is what I get.


~$ sudo mkdir /media/hda1 /media/hda2 /media/hdb1
mkdir: cannot create directory `/media/hda1': File exists
mkdir: cannot create directory `/media/hda2': File exists
mkdir: cannot create directory `/media/hdb1': File exists
~$ sudo mount -a
mount: /dev/hda1 already mounted or /media/windows busy
mount: according to mtab, /dev/hda1 is mounted on /media/hda1
~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb2              75G  3.1G   68G   5% /
varrun                760M   80K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
procbususb             10M  140K  9.9M   2% /proc/bus/usb
udev                   10M  140K  9.9M   2% /dev
devshm                760M     0  760M   0% /dev/shm
lrm                   760M   18M  743M   3% /lib/modules/2.6.17-10-generic/volatile
/dev/hdc              4.4G  4.4G     0 100% /media/cdrom0
/dev/hda1             5.6G  4.6G  941M  84% /media/hda1
/dev/hda2             148G   34G  114G  23% /media/hda2
/dev/hdb1              71G   14G   57G  20% /media/hdb1

Should I be ready to go?
I look in my file browser and see an empty folder for "FAT_files"

next steps?

---

### Post by taurus on 2007-02-01
Looks like you have mounted /dev/hda1 to /media/windows.  Therefore, you need to decide whether you want to mount /dev/hda1 or /media/windows or to /media/hda1.  If you want to mount it to /media/windows, then remove the entry for /media/hda1 in /etc/fstab.  But if you want to mount it to /media/hda1, then remove the entry for /media/windows.  And if you are still not sure, just post your /etc/fstab here then.

```
cat /etc/fstab
```

---

### Post by cmk_78212 on 2007-02-01
I don't know which would be better.  Any ideas?


By the way, I am getting XGL running so I am feeling a little woozy right now:)

---

### Post by taurus on 2007-02-01
Personally, I would mount it to /media/hda1 so it would be similar with the other two partitions that you have just added.

p.s.  Better not driving tonight then!

---

### Post by cmk_78212 on 2007-02-01
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=ef34ff9b-e6c6-4f2f-8a08-66f544c256cd /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=c8d2e900-c520-45cf-82f3-b91b8afd9ff4 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdf        /media/floppy1  auto    rw,user,noauto  0       0
/dev/hda1   /media/hda1   vfat   iocharset=utf8,umask=000   0   0
/dev/hda2   /media/hda2   ntfs   nls=utf8,umask=0222   0   0
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0

I took out the media/windows line
This is what I have now.  Still no change in the file browser.
Where to I look for my files?

---

### Post by taurus on 2007-02-01
Do you see three little icons on your desktop?  

Or you can use nautilus to browse to /media and you will see your partitions there.

---

### Post by cmk_78212 on 2007-02-01
It works!  Any down side to changing there name and placing on the desktop?

---

### Post by cmk_78212 on 2007-02-01
Also, how good are you at getting windows decorators to work in xgl?

---

