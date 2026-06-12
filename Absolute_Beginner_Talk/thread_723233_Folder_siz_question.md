---
title: "Folder siz question"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by mistux on 2008-03-13
I just installed a second hard drive and it is 120 gig, the boot one is 16 gig.

When I go to properties on any folder on either drive is says " free Space 9.1 gig"

What is that telling me?  And how can I get it to be more?

---

### Post by finer recliner on 2008-03-13
there are no C:/ and D:/ (etc) drives in linux. every device is mounted somewhere under the root directory (/)

type this command in the terminal to see the actual free space of your drives 
```
df -h
```

/ is probably your boot drive of 16GB. your 120GB drive is probably mounted somewhere on /media/

enjoy

---

### Post by mistux on 2008-03-13
When I do the df -h I get:

```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G  3.7G  9.2G  29% /
varrun                125M   96K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   52K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   34M   91M  28% /lib/modules/2.6.22-14-generic/volatile

```

and I don't see the 120 gig drive which I think should be listed as /dev/sdb (which is what I wrote down when I installed it)

---

### Post by finer recliner on 2008-03-13
are you sure that the 160GB drive is mounted?

what is the output of 
```
sudo fdisk -l
```
and
```
mount
```

---

### Post by mistux on 2008-03-13
> **finer recliner said:**
> are you sure that the 160GB drive is mounted?

what is the output of 
```
sudo fdisk -l
```
and
```
mount
```

Here is the output for fdisk -l:

```
Disk /dev/sda: 15.3 GB, 15382241280 bytes
255 heads, 63 sectors/track, 1870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e38e78c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1786    14346013+  83  Linux
/dev/sda2            1787        1870      674730    5  Extended
/dev/sda5            1787        1870      674698+  82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

and here it is for mount:

```
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

[COLOR="Red"]BUT,[/COLOR] it should have a partition, here is the output from what I did (I saved all my commands luckily)

```

sudo mke2fs -cv /dev/sdb
mke2fs 1.40.2 (12-Jul-2007)
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
15007744 inodes, 30015216 blocks
1500760 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
916 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872

Running command: badblocks -b 4096 -X -s /dev/sdb 30015215
Checking for bad blocks (read-only test): done                                
Writing inode tables: done                            
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 29 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to overrid
```

[COLOR="Red"]THEN,[/COLOR] I  added the lines to:  /etc/fstab 

```
 
/dev/sdb	/media/picstore ext3	defaults 	0 	0 
```

---

### Post by finer recliner on 2008-03-13
just use gparted to reformat the 160GB drive. its much easier.

(you will lose any data that already existed on it. though i dont see how you could access it right now anyways without a valid filesystem on it).

---

### Post by mistux on 2008-03-13
OK, used gparted and now I have:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G  3.7G  9.2G  29% /
varrun                125M   96K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   52K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   34M   91M  28% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             113G   60M  107G   1% /media/disk

```

 :) and at the bottom is my new disk: 
[COLOR="Red"]/dev/sdb1             113G   60M  107G   1% /media/disk[/COLOR]

(although it is formated at Ext2 and not 3 like the primary, even though I selected 3)  

Now, is there anything else I need to do to use it?  Do I have to chmod it or anything?

---

### Post by finer recliner on 2008-03-13
glad to see you got it recognized and mounted :)

you should set the permissions for a storage drive in your fstab file. that way the same permissions will be applied every time you boot up.

more info how to edit your fstab:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by mistux on 2008-03-24
Well I don't think I have everything just right, but I think I am close.

My new second hard disk works and I have copied over about 30 gig of files to it, but In order to use it and before my Gallery2 photo site can use it, I have to double click on it in the "Computer--File Browser" then I have to give it my password becasue it comes up with:  ```
Access to this internal disk is restricted to system administrators for security reasons. 
```

I did try to make an entry in the ftab of:
```
/dev/sdb1 	/media/Disk	ext2	defaults	0	1
```
But that did not seem to do anything.

What did I do wrong?

---

