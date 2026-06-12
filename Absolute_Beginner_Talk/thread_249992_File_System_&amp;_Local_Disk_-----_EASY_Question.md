---
title: "File System &amp; Local Disk ----- EASY Question"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2006-09-03
Here is a pic of my desktop.  I am very new to linux and am confused.  

I am confused because the "File System" is listed as another drive, but isn't it really part of the "Local Disk?"  Does Ubuntu seperate them since my home folder is under the File System.  It in a way, keeps me from messing up/accidently deleting sometihng from my main Local Disk?   Thank you very much for any input.

[IMG]http://i53.photobucket.com/albums/g56/learntobndg/desktopubuntu.png[/IMG]

---

### Post by csy on 2006-09-03
its the other way around

your local disk is part of the filesystem

every device that gets  mounted will be part of some folder in the filesystem

i think its part of the "everything is a file" concept

it wont keep you from deleting things. its more a shortcut to special folders(places) on the left side

---

### Post by meng on 2006-09-03
Yes, as csy says, the file system is not completely separate from the other items listed in Places. Perhaps you are thinking in Windows mode, where C: and D: are separate drives (or at least separate partitions). In Linux, everything is within the filesystem (mountpoint /, sometimes called root although I find that confusing since we also talk about root user/privileges). Many people put /home on a separate partition (an excellent idea), but regardless of whether its on the same partition or not, it's considered integrated within the / filesystem. Are you confused yet?

---

### Post by 3rr0r on 2006-09-03
> **meng said:**
> Yes, as csy says, the file system is not completely separate from the other items listed in Places. Perhaps you are thinking in Windows mode, where C: and D: are separate drives (or at least separate partitions). In Linux, everything is within the filesystem (mountpoint /, sometimes called root although I find that confusing since we also talk about root user/privileges). Many people put /home on a separate partition (an excellent idea), but regardless of whether its on the same partition or not, it's considered integrated within the / filesystem. Are you confused yet?

Ya, I was thinking via windows where this is "C" and this is "D", they are seperate partitions.  So basically, the file system is the whole enchilada?  Everything falls under the file system which is why I can also see SDA4 which is a fat32 drive.  I was just making sure everything I plan on saving to the hard drive was really writing to the partition I wanted it to.  It threw me off when File System and Local Disk were seperate (me thinking seperate drives).

Does that sound right?

---

### Post by meng on 2006-09-03
Yes even sda4 will be under the filesystem somewhere (once it is mounted), possibly under /media/sda4. Think of / as being "My Computer".

---

### Post by Miademora on 2006-09-03
In Gnome Administration -> Disks should show where everything is in the Filesystem

Also "mount" in any console terminal

---

### Post by 3rr0r on 2006-09-03
isn't sda4 mounted already?  I guess I am a little confused with that terminology.  I have come to think that mounted means it is "mapped" to the right location so that the file system knows where it is and what kind of file type it is (fat32, ext3, ntfs, etc).  

I see what you mean mia, that every disk falls uder the file system.

Did "mount" in the terminal and this is what I got:

/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda4 on /media/sda4 type vfat (rw,utf8,umask=007,gid=46)


any ideas?

---

### Post by meng on 2006-09-03
It may already be mounted, depends on your setup. Some drives/partition, whether removable or not, are automatically mounted if found. Others aren't. Your concept of what mounted means is essentially correct. A mounted drive is there and immediately ready for access. An unmounted drive is there, but not ready to be read from or written to (until it is mounted).

---

### Post by Miademora on 2006-09-03
> **3rr0r said:**
> 
/dev/sda4 on /media/sda4 type vfat (rw,utf8,umask=007,gid=46)


Yes it is mounted as /media/sda4 in your Filesystem

---

### Post by 3rr0r on 2006-09-03
I don't see my mandy drive (sda5).  Is this because I went into the /etc/fstab and put a # next to the code relating to sda5 because I didn't want it on my desktop in ubuntu?  Hence, doing mount, it does not "see" the drive.

---

### Post by Miademora on 2006-09-03
Putting a # in front of something leads to the command not getting processed. So yes its your "fault". :wink: 

Mount shows only the current "mapped" Devices. "sudo fdisk -l" should show what Devices are available.

---

### Post by 3rr0r on 2006-09-03
So, if I want to be able to write to my mandy drive (sda5) but I don't want the drive sitting on my desktop in ubuntu.... how would I go about doing that?  Also I ran the command you gave me

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2805    22531131    7  HPFS/NTFS
/dev/sda2            2806        5992    25599577+   5  Extended
/dev/sda3            5993        8542    20482875   83  Linux
/dev/sda4            8543        9705     9341797+   b  W95 FAT32
/dev/sda5            2806        5355    20482843+  83  Linux
/dev/sda6            5356        5992     5116671   82  Linux swap / Solaris

---

### Post by Miademora on 2006-09-03
Only option i found so far would be to turn it off for all drives. Maybe someone knows a better/easier way.

Open "gconf-editor" in terminal or somewhere else. Go to apps->nautilus->desktop and uncheck "volumes_visible".

---

### Post by jfighter on 2006-09-19
I can't mount my C: local drive from the Ubuntu Desktop Live CD.  I think the problem has to do with permissions or something...even when I do a 'sudo mount', I don't get error messages but nothing is mounted.

Does anyone know of a way for me to mount both my local C: drive and my external USB drive with a Live CD (of any Linux distro)?  (I need this to recover a backup image)

Thanks

---

### Post by 3rr0r on 2006-09-19
Can you give the output to your fstab file?

---

### Post by CatKiller on 2006-09-19
> **3rr0r said:**
> So, if I want to be able to write to my mandy drive (sda5) but I don't want the drive sitting on my desktop in ubuntu.... how would I go about doing that?  

make a directory somewhere other than in /media and change your /etc/fstab to mount /dev/sda5 to the new directory. You only get drives mounted in /media showing on your desktop.

For example, my /etc/fstab includes these lines:
> 
/dev/hda3       /data/fat           vfat    iocharset=utf8,umask=000        0
    0
/dev/hdb5       /data/ntfs      ntfs    nls=utf8,umask=0222 0       0
/dev/hdb6       /music          ntfs    nls=utf8,umask=0222 0       0


and none of these show on the desktop.

---

### Post by martinja on 2007-11-24
> **meng said:**
>  In Linux, everything is within the filesystem (mountpoint /, sometimes called root although I find that confusing since we also talk about root user/privileges). Many people put /home on a separate partition (an excellent idea), but regardless of whether its on the same partition or not, it's considered integrated within the / filesystem. Are you confused yet?

I have a secondary harddrive that is currently called LOCAL DISK and I want to put my /home directory on it. How can I do this so that the server and operating system know about it and I can access it from Terminal.
I hope this makes sense.

---

