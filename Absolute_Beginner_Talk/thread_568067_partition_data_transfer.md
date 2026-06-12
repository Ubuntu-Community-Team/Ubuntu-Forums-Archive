---
title: "partition data transfer?"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by iamthemicrowave on 2007-10-05
I was running Windows XP, and I recently partitioned my hard drive in half to run Ubuntu.  I partioned it during the installion of Ubuntu. I am a first time linux user.  Is there a way to transfer my files from my XP partition to the Ubuntu partition? Thanks.


sudo /sbin/fdisk -l outputs

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          14      112423+  de  Dell Utility
/dev/sda2   *          15        5944    47632725    7  HPFS/NTFS
/dev/sda3            5945       11901    47849602+  83  Linux
/dev/sda4           11902       12161     2088450    5  Extended
/dev/sda5           11902       12161     2088418+  82  Linux swap / Solaris

sudo mount

/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

---

### Post by hyper_ch on 2007-10-05
There are multiple ways:

(1) using a FAT32 partition - both, windows and linux, can by default read and write to FAT32
(2) by default Linux can only read NTFS drives. so you should be able to copy from the windows drive to your linux partition. If you want also to write to ntfs, then you have to install ntfs-3g
(3) By default, Windows cannot read/write Ext3 partitions. You can install this here ( [http://www.fs-driver.org/](http://www.fs-driver.org/) ) to also make windows able to read/write ext3

---

### Post by iamthemicrowave on 2007-10-05
Could I have more detailed instructions please?

---

### Post by Discov3ry on 2007-10-05
Post the output of (run these from the terminal):

sudo /sbin/fdisk -l

and

sudo mount

---

### Post by bsharp on 2007-10-05
```
sudo su
mkdir /media/windows
mount /dev/whatever your windows partition is e.g. hda1, sda3
nautilus
```

that will open nautilus with root privileges which can be *very* destructive.  navigate to where the windows drive is mounted (/media/windows) and drag-and-drop to your other partition (such as your desktop or home folder)

---

### Post by iamthemicrowave on 2007-10-05
updated first post

---

### Post by Discov3ry on 2007-10-05
Assuming that /dev/sda2 is your windows partition:

#cd /media
#mkdir windows
#mount -t ntfs /dev/sda2 /media/windows
#mount (to verify that it mounted correctly)

Go to: Places -> Computer -> Filesystem -> media -> windows

If you don't want to redo this every time you reboot update the /etc/fstab file with:

/dev/sda2                   /media/windows                    ntfs   defaults,ro        0 0

(I'm on RedHat now, so your fstab entry for ntfs may differ a little but this I think should work ok)

Happy moving!

---

### Post by iamthemicrowave on 2007-10-05
> **Discov3ry said:**
> 
#cd /media
#mkdir windows
#mount -t ntfs /dev/sda2 /media/windows
#mount (to verify that it mounted correctly)

What do these lines mean, and where do they go?

---

### Post by Discov3ry on 2007-10-05
> **iamthemicrowave said:**
> What do these lines mean, and where do they go?

These commands:
sudo cd /media
sudo mkdir windows
sudo mount -t ntfs /dev/sda2 /media/windows
sudo mount 
(to verify that it mounted correctly)

should be executed on the command line (terminal). I modified them so you can copy/paste.

---

### Post by iamthemicrowave on 2007-10-05
Oh, OK. Thank you very much. I am still having problems 

sudo cd /media

sudo: cd: command not found


sudo mkdir windows

mkdir: cannot create directory `windows': File exists


sudo mount -t ntfs /dev/sda2 /media/windows

mount: mount point /media/windows does not exist


sudo mount

/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda2 on /media/disk type ntfs (rw,nosuid,nodev,umask=222,utf8)

---

### Post by Discov3ry on 2007-10-05
> **iamthemicrowave said:**
> Oh, OK. Thank you very much. I am still having problems 

sudo cd /media

sudo: cd: command not found


sudo mkdir windows

mkdir: cannot create directory `windows': File exists


sudo mount -t ntfs /dev/sda2 /media/windows

mount: mount point /media/windows does not exist


sudo mount

/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda2 on /media/disk type ntfs (rw,nosuid,nodev,umask=222,utf8)

Never mind the whole procedure! (and please ignore the sudo cd :) )
It appears as the NTFS partition is already mounted under /media/disk

So using Nautilus navigate to /media/disk and you should be able to see all your windows files.

---

### Post by iamthemicrowave on 2007-10-07
Yes I was able to complete it successfully, thank you.  Is it possible for me to rename the different partitions so I can keep them separated in my head?

---

### Post by Discov3ry on 2007-10-09
You can assign labels to partitions with the 'e2label -L device label_name' command, assuming you're using ext2 or ext3 file system type. 

For other file systems such as NTFS you can simply mount them in any directory named whatever you like.

---

