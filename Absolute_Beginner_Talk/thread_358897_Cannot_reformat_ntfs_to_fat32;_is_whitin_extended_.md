---
title: "Cannot reformat ntfs to fat32; is whitin extended volume also containing linux-swap"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2007-02-11
I want to reformat my ntfs partition to fat32 so I can access it from both windows and ubuntu. But Gparted does not do anything because it says that:

"At least one operation was applied to a busy device. 
A busy device is a device with at least one mounted partition. Because making changes to a busy device may confuse the kernel, you are advised to reboot your computer."

My whole computer is partitioined like this:
Partition 1 (NTFS) with windows installed
Partition 2 (extended) containing two other partitions one being NTFS and one linux swap
Partition 3 (ext3) containing ubuntu

What can I now do to reformat the ntfs partition within the extended part to a fat32 format?

---

### Post by taurus on 2007-02-11
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by igknighted on 2007-02-11
You need to unmount the NTFS partition in order to format it.  Try:
```
sudo umount /dev/<partition>
```
where partition might be, say sda5 or hda5, whatever one is the NTFS partition

---

### Post by kramer65 on 2007-02-11
The output is this:

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5216    41897488+   7  HPFS/NTFS
/dev/hda2            5217       19898   117933165    f  W95 Ext'd (LBA)
/dev/hda3           19899       24321    35527747+  83  Linux
/dev/hda5            5217       19706   116390893+   b  W95 FAT32
/dev/hda6           19707       19898     1542208+  82  Linux swap / Solaris

So what do I need to do? do "sudo umount /dev/hda5", or something else?

---

### Post by taurus on 2007-02-11
What partition do you want to reformat, /dev/hda1 or /dev/hda5?

---

### Post by kramer65 on 2007-02-11
I want to reformat hda5. 
on hda1 is my windows which I want to keep..(for now.. :-))

---

### Post by taurus on 2007-02-11
But /dev/hda5 is already a fat32/vfat format.

---

### Post by kramer65 on 2007-02-11
huh? hey your right..

But how can I then access the volume?

If I go to places > computer, and click on 111.0 GB volume, it says:
"Unable to mount the selected volume
error: device /dev/hda5 is not removable
error: could not execute pmount

what to do now?

---

### Post by taurus on 2007-02-11
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hda5   /media/hda5   vfat   iocharset=utf8,umask=000   0   0
```
Save the change and create a new mount point and mount it.

```
sudo mkdir /media/hda5
sudo mount -a
df -h
```

---

### Post by kramer65 on 2007-02-11
ok thanks. All what you said is pretty much greek to me. But I just did what you said. When I now go to places > computer and click on 111.0GB Volume it says:

"Unable to mount the selected volume
mount: only root can mount /dev/hda5 on /media/hda5

ehmm. I almost don't dare to ask, but.. what now?

---

### Post by taurus on 2007-02-11
What's the output of this command from a terminal?

```
df -h
```

---

### Post by kramer65 on 2007-02-11
The output of that is the following:

Filesystem            Size Used Avail Use% Mounted on
/dev/hda3              34G   32G  501M  99% /
varrun                506M   88K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  192K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-28-386/volatile

Does that help?

---

### Post by taurus on 2007-02-11
Did you follow all the steps in my previous post?  What's your /etc/fstab look like now?

```
cat /etc/fstab
```

---

### Post by kramer65 on 2007-02-11
The output of that is this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda5   /media/hda5   vfat   iocharset=utf8,umask=000   0   0

I did do all the steps you told me, but the first one did give me some kind of error, but it did open the window mwith all the text. So I just saved the last line in that (what you told me)...

---

### Post by taurus on 2007-02-11
And did you run the last three commands from a terminal?

```
sudo mkdir /media/hda5
sudo mount -a
df -h
```

---

### Post by kramer65 on 2007-02-11
Yes I did,

I just ran it again, and I now get: mkdir: cannot create directory `/media/hda5': File exists

---

### Post by taurus on 2007-02-11
Run these two commands again and paste the output of the second one here.

```
sudo mount -a
df -h
```

---

### Post by kramer65 on 2007-02-11
This is the output:

ricam@ricom:~$ sudo mount -a
Password:
ricam@ricom:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/hda3              34G   32G  478M  99% /
varrun                506M   88K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  192K  506M   1% /dev
devshm                506M   16K  506M   1% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-28-386/volatile
/dev/hda5             111G   16K  111G   1% /media/hda5

---

### Post by taurus on 2007-02-11
Well, /dev/hda5 is now mounted to /media/hda5.  You should see an icon on your desktop for /dev/hda5 now.

And looks like there is nothing on it.

```
/dev/hda5 111G 16K 111G 1% /media/hda5
```

---

