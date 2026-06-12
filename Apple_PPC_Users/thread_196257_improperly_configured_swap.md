---
title: "improperly configured /swap?"
date: 2006-06-13
forum: Apple PPC Users
---

### Post by swartzfeger on 2006-06-13
Hi all,

Could someone take a look at a screenshot of my partions [here]("http://www.box.net/public/vsuxo3a78z").

The screenshot shows that my filesystem/ext3 is /dev/sdc5 and is enabled (labeled green). My /swap is listed as /dev/sdc6 and is disabled (labeled gray).

Here's the thing: I don't *have* a /dev/sdc*, just an sda and sdb.

sudo fdisk -l gives me the following:

[SIZE="3"][FONT="Courier New"]/dev/sdb
        #                    type name                  length   base      ( size )  system
/dev/sdb1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sdb2         Apple_Bootstrap Apple_HFS_Untitled_1      8192 @ 64        (  4.0M)  NewWorld bootblock
/dev/sdb3         Apple_Bootstrap untitled                1954 @ 3041864   (977.0k)  NewWorld bootblock
/dev/sdb4         Apple_UNIX_SVR2 Apple_HFS_Untitled_2   2771464 @ 270400    (  1.3G)  Linux native
/dev/sdb5         Apple_UNIX_SVR2 untitled           150615235 @ 3043818   ( 71.8G)  Linux native
/dev/sdb6         Apple_UNIX_SVR2 swap                 6427475 @ 153659053 (  3.1G)  Linux swap
/dev/sdb7              Apple_Free Extra                 262144 @ 8256      (128.0M)  Free space

Block size=512, Number of Blocks=160086528
DeviceType=0x0, DeviceId=0x0[/FONT]
[/SIZE]

As listed with fdisk, my /swap is /dev/sdb6, and I'm guessing my filesystem should be /dev/sdb5 (I think).

Are my partition mappings messed up? Disk & Filesystems is showing one thing, and fdisk shows another. Could this explain my system's overall subpar performance?

Thanks!

---

### Post by tidris on 2006-06-14
What do you get when you type these commands in a terminal window:

cat /etc/fstab

ls /dev/sd*

sudo fdisk -l /dev/sdc

---

### Post by swartzfeger on 2006-06-14
[QUOTE=tidris]What do you get when you type these commands in a terminal window:

cat /etc/fstab

ls /dev/sd*

sudo fdisk -l /dev/sdc[/QUOTE]

Thanks Tidris, I'll run these when I get home tonight!

---

### Post by swartzfeger on 2006-06-14
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/sdc5 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
/dev/sdc6 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0

jay@linux:~$ ls /dev/sd*
/dev/sda    /dev/sda2  /dev/sda5  /dev/sda8  /dev/sdb1  /dev/sdb4  /dev/sdb7
/dev/sda1   /dev/sda3  /dev/sda6  /dev/sda9  /dev/sdb2  /dev/sdb5  /dev/sdc
/dev/sda10  /dev/sda4  /dev/sda7  /dev/sdb   /dev/sdb3  /dev/sdb6  /dev/sdc1

sudo fdisk -l /dev/sdc didn't seem to do anything...

---

### Post by tidris on 2006-06-15
[QUOTE=swartzfeger]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/sdc5 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
/dev/sdc6 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0

jay@linux:~$ ls /dev/sd*
/dev/sda    /dev/sda2  /dev/sda5  /dev/sda8  /dev/sdb1  /dev/sdb4  /dev/sdb7
/dev/sda1   /dev/sda3  /dev/sda6  /dev/sda9  /dev/sdb2  /dev/sdb5  /dev/sdc
/dev/sda10  /dev/sda4  /dev/sda7  /dev/sdb   /dev/sdb3  /dev/sdb6  /dev/sdc1

sudo fdisk -l /dev/sdc didn't seem to do anything...[/QUOTE]
I am no expert, but it looks to me like the "partitions.png" picture matches the info above for the most part. Apparently you do have a third disk, sdc, and during the ubuntu installation it was selected for use as root in partition 5 (/dev/sdc5) and swap in partition 6 (dev/sdc6). However, it appears that disk sdc only has one partition in it, and it is being used as the root. That isn't good I think. A disk ought to have the partition map in partition 1, and maybe that is the reason fdisk couldn't show a partition list for sdc?

If anybody has a better explanation I would like to hear it. This is really weird.

---

### Post by nkbj on 2006-06-15
[QUOTE=swartzfeger]Are my partition mappings messed up? Disk & Filesystems is showing one thing, and fdisk shows another. Could this explain my system's overall subpar performance?[/QUOTE]

The swap partition will not show up as a filesystem as it is actually handled as memory. Could you please give us the output from the 'free' command?

---

### Post by tidris on 2006-06-15
What do you get when you type these commands in a terminal window:

sudo mount /dev/sdb5  /mnt

cat /etc/mtab

ls /mnt

sudo umount /mnt

---

### Post by swartzfeger on 2006-06-15
[QUOTE=tidris]I am no expert, but it looks to me like the "partitions.png" picture matches the info above for the most part. Apparently you do have a third disk, sdc, and during the ubuntu installation it was selected for use as root in partition 5 (/dev/sdc5) and swap in partition 6 (dev/sdc6). However, it appears that disk sdc only has one partition in it, and it is being used as the root. That isn't good I think. A disk ought to have the partition map in partition 1, and maybe that is the reason fdisk couldn't show a partition list for sdc?

If anybody has a better explanation I would like to hear it. This is really weird.[/QUOTE]

Well, I do have a third disk -- a firewire drive -- but I specifically shut it down during the installation so as not to get it involved in the mix (or at least I thought I shut it down, perhaps I didn't).

When I'm at home tonight, I'll run these commands again with the firewire disk turned off and disconnected to make sure it isn't sdc.

Also, nkbj -- do I simply type 'free' in the Konsole?

---

### Post by nkbj on 2006-06-15
[QUOTE=swartzfeger]Also, nkbj -- do I simply type 'free' in the Konsole?[/QUOTE]
Yes

---

### Post by swartzfeger on 2006-06-15
[QUOTE=tidris]What do you get when you type these commands in a terminal window:

sudo mount /dev/sdb5  /mnt[/QUOTE]

appeared to do nothing

> cat /etc/mtab

/dev/sdc5 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
/dev/sdb5 /mnt ext3 rw 0 0

> ls /mnt

bin   cdrom  etc   initrd  lost+found  mnt  proc  sbin  sys  usr
boot  dev    home  lib     media       opt  root  srv   tmp  var

> sudo umount /mnt

Didn't appear yo do anything.

Thanks for any help!

---

### Post by swartzfeger on 2006-06-15
[QUOTE=nkbj]The swap partition will not show up as a filesystem as it is actually handled as memory. Could you please give us the output from the 'free' command?[/QUOTE]

[FONT="Fixedsys"]            
Mem:       1768572     396264    1372308          0      52072     184840
-/+ buffers/cache:     159352    1609220
Swap:            0          0          0
[/FONT]

---

### Post by tidris on 2006-06-15
Ok, so I think you can fix the swap issue by editing /etc/fstab. Just change the line that starts with /dev/sdc6 to be /dev/sdb6. That should be fairly safe to do. You will need to use sudo.

As for where the root partition is, I wonder what happened when you disconnected the firewire disk from the computer. Were you able to boot? Did sdc dissapear?

---

### Post by swartzfeger on 2006-06-16
[QUOTE=tidris]Ok, so I think you can fix the swap issue by editing /etc/fstab. Just change the line that starts with /dev/sdc6 to be /dev/sdb6. That should be fairly safe to do. You will need to use sudo.

As for where the root partition is, I wonder what happened when you disconnected the firewire disk from the computer. Were you able to boot? Did sdc dissapear?[/QUOTE]

Thanks tidris, editing /etc/fstab worked for /swap! It now shows correctly in Disks & Filesystems, and also displays correctly with free, etc.

After doing the swap edit, I shutdown and disconnected my firewire drive completely. Upon restart, here's what I saw:

cat /etc/mtab
/dev/sdc5 / ext3 rw,errors=remount-ro 0 0

cat /etc/fstab
/dev/sdc5 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1

ls /dev/sd* -- this time, no /dev/sdc shows up
/dev/sda    /dev/sda2  /dev/sda5  /dev/sda8  /dev/sdb1  /dev/sdb4  /dev/sdb7
/dev/sda1   /dev/sda3  /dev/sda6  /dev/sda9  /dev/sdb2  /dev/sdb5
/dev/sda10  /dev/sda4  /dev/sda7  /dev/sdb   /dev/sdb3  /dev/sdb6

would it hurt to edit my /etc/fstab and change it to /dev/sdb5?

---

### Post by tidris on 2006-06-16
[QUOTE=swartzfeger]

would it hurt to edit my /etc/fstab and change it to /dev/sdb5?[/QUOTE]
I think it will be OK. The reason I asked you to mount /dev/sdb5 earlier was to see if it had the ussual LINUX directories in it, and it does. If things go wrong, you can always boot from the Desktop CD and change fstab to the way it was.

---

### Post by nkbj on 2006-06-16
You should also add this line to /etc/fstab:

/dev/sdb6 none swap sw 0 0

When you have saved /etc/fstab try running 'sudo swapon -a' and 'free' in a terminal, then 'Swap:' should something else than '0 0 0' in the output from 'free'.

---

### Post by swartzfeger on 2006-06-16
[QUOTE=nkbj]You should also add this line to /etc/fstab:

/dev/sdb6 none swap sw 0 0

When you have saved /etc/fstab try running 'sudo swapon -a' and 'free' in a terminal, then 'Swap:' should something else than '0 0 0' in the output from 'free'.[/QUOTE]

nkbj,

/dev/sdb6 none swap sw 0 0 was already in my /etc/fstab

my free now reads

Swap:      3213728          0    3213728

tidis/nkbj -- thanks so much for your help!

---

