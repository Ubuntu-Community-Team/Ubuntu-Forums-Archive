---
title: "[SOLVED] Lost 'Local Drive'"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by lemon_duck on 2008-01-31
My system has two Hard Drives installed. The slave is used to archive .avi files

This drive will eventually be made accessible to a future network allowing files to be exchanged between computers.

Prior to downloading and installing WINE and uTorrent the drive was visible on desktop and was accessible by inputting my password.

Now the drive cannot be found and accessed.

How do I cause it to become 'visible' again?

---

### Post by emarkd on 2008-01-31
It should be mounted under /media.  Check and see if you can find it there.

BTW:  A great torrent client for Linux is rtorrent.  Yes, there's a steep learning curve, but I think it's worth it.  But hey, use what works for you!

---

### Post by jan quark on 2008-01-31
what do these terminal commands give as the result?

```
mount
```
```
ls /dev/disk/by-id -lah
```

---

### Post by lemon_duck on 2008-01-31
I used Command as suggested by Jan Quark. Doesn't mean anything to me. Assistance required.
Thanks for the tip re rtorrent, Emarkd.


dave@dave-desktop:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
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
dave@dave-desktop:~$ ls /dev/disk/by-id -lah
total 0
drwxr-xr-x 2 root root 180 2008-01-31 11:14 .
drwxr-xr-x 6 root root 120 2008-01-31 11:14 ..
lrwxrwxrwx 1 root root   9 2008-01-31 11:14 ata-Maxtor_6Y160P0_Y47KX1DE -> ../../hda
lrwxrwxrwx 1 root root  10 2008-01-31 11:14 ata-Maxtor_6Y160P0_Y47KX1DE-part1 -> ../../hda1
lrwxrwxrwx 1 root root  10 2008-01-31 11:14 ata-Maxtor_6Y160P0_Y47KX1DE-part2 -> ../../hda2
lrwxrwxrwx 1 root root  10 2008-01-31 11:14 ata-Maxtor_6Y160P0_Y47KX1DE-part5 -> ../../hda5
lrwxrwxrwx 1 root root   9 2008-01-31 11:14 ata-RRW_4x4x24_4VO0927DE11327 -> ../../hdd
lrwxrwxrwx 1 root root   9 2008-01-31 11:14 ata-ST380021A_3HV1AA3K -> ../../hdb
lrwxrwxrwx 1 root root  10 2008-01-31 11:14 ata-ST380021A_3HV1AA3K-part1 -> ../../hdb1

---

### Post by lemon_duck on 2008-01-31
I checked under media as suggested by Emarkd, it isn't there.:-k

---

### Post by jan quark on 2008-01-31
ok here we go

next command

```
sudo fdisk -l
```
pls post result

what are we doing now
?

we want to mount your missing drive 
the command above lists all your partitions mounted or not

then we mount according to this scheme
```

$ mount /dev/name of device /mnt/location where the files should be accessed 
```

for example to mount a floppy disk we do the following

```
$ mount /dev/fd0 /mnt/floppy
```

---

### Post by lemon_duck on 2008-01-31
Thanks Jan Qwark. This is the result.


dave@dave-desktop:~$ sudo fdisk -l
[sudo] password for dave:



Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e697e69

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19080   153260068+  83  Linux
/dev/hda2           19081       19457     3028252+   5  Extended
/dev/hda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf64cf64

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9729    78148161    7  HPFS/NTFS
dave@dave-desktop:~$

---

### Post by jan quark on 2008-01-31
try this

```
mount /dev/hdb /mnt/hdb
```

and post all error messages :))

---

### Post by jan quark on 2008-01-31
and make sure you have ntfsporgs installed, this is needed to mount ntfs partitions

```
sudo apt-get install ntfsporgs
```

---

### Post by lemon_duck on 2008-01-31
In the interim I tried installing the floppy and got this same messasge

dave@dave-desktop:~$ mount /dev/hdb /mnt/hdb
mount: only root can do that
dave@dave-desktop:~$

---

### Post by jan quark on 2008-01-31
```
sudo mount /dev/hdb /mnt/hdb
```

the sudo part sets the superuser rights to you, the root rights

---

### Post by lemon_duck on 2008-01-31
Also tried installing ntfsporgs with this result.

dave@dave-desktop:~$ sudo apt-get install ntfsporgs
[sudo] password for dave:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfsporgs
dave@dave-desktop:~$

---

### Post by lemon_duck on 2008-01-31
Result

dave@dave-desktop:~$ sudo mount /dev/hdb /mnt/hdb
mount: mount point /mnt/hdb does not exist
dave@dave-desktop:~$

---

### Post by jan quark on 2008-01-31
you know these days where nothing works:)


ok back to work
open the synaptic package manager
and type ntfs into the search

now check if these two packages are available and installed 
ntfs-3g
ntgsprogs

install them if you can :)

---

### Post by jan quark on 2008-01-31
```
sudo mkdir /mnt/hdb
```

this code will create the missing mount point

---

### Post by lemon_duck on 2008-01-31
ntfs-3g was installed
ntgsprogs (and a linked package) now installed.

I've been summoned to table, back shortly

---

### Post by jan quark on 2008-01-31
hey no problem 
I have read somewhere that food is important for a wealthy state of mind
I will read something about mounting in the meantime

---

### Post by lemon_duck on 2008-01-31
The only entry I could find in 'Ubuntu for non Geeks' related to Windows partitions.

---

### Post by jan quark on 2008-01-31
did you succeed in creating the mount point and mounting the drive?

---

### Post by lemon_duck on 2008-01-31
No but if you reckon the information will be under that heading I'll  give it a try.

(After the dogs are walked and the rubbish put out).

---

### Post by jan quark on 2008-01-31
so I just wanted to recapitulate the info and bring some order in my brainstorming 



0.
install the needed and above mentioned apps

1.
```
sudo mkdir /mnt/hdb
```
2.
```
sudo mount /dev/hdb /mnt/hdb
```

---

### Post by lemon_duck on 2008-01-31
Sorry I lost the place there for a minute or 60.

dave@dave-desktop:~$ sudo mkdir /mnt/hdb
[sudo] password for dave:
dave@dave-desktop:~$ 

I've found the Drive in the Device Manager but  both Vendor and Device are listed as unknown and device type "volume" "block" and capabilities volume block

---

### Post by lemon_duck on 2008-01-31
I don't know if this helps

dave@dave-desktop:~$  sudo mkdir /mnt/hdb
mkdir: cannot create directory `/mnt/hdb': File exists
dave@dave-desktop:~$

---

### Post by lemon_duck on 2008-01-31
We got out of step a bit:

dave@dave-desktop:~$ sudo mount /dev/hdb /mnt/hdb
mount: you must specify the filesystem type
dave@dave-desktop:~$

---

### Post by Rocket2DMn on 2008-01-31
You need to mount the partition, not the device itself
```
sudo mount /dev/hdb1 /mnt/hdb -t ntfs-3g
```
You may need to enable writing to ntfs by installing ntfsprogs
```
sudo apt-get install ntfsprogs
```
to enable writing: ```
gksudo ntfs-config
``` (unmount the drive before doing this)

---

### Post by lemon_duck on 2008-01-31
Okey and thanks for the input. Hello Rocket2DMn.

U still there jan quark ?

What is the code for unmount?

sudo mkdir /unmnt/hdb

---

### Post by jan quark on 2008-01-31
I am here

the code for unmounting is
```

sudo unmount /dev/name-of-partition
```

---

### Post by Rocket2DMn on 2008-01-31
unmount would be the command "umount" not "unmount"
```
sudo umount /mnt/sdb
or
sudo umount /dev/sdb1
```
That is to say, you can either unmount by specifying the device OR it's mount point.
/mnt/hdb is a folder on your root file system.  If you open "/" you will see a folder called "mnt" with a subfolder called "hdb" which you created.  When you have the drive mounted, you will see the contents of your other hard drive in that directory.
jan is the one who asked me to come in here and help you :)
I'll check up on you in a few hours, good luck!

---

### Post by jan quark on 2008-01-31
I am here

the code for unmounting is
```

sudo umount /dev/name-of-partition
```


soooory for the typo have detected it after submitting

---

### Post by lemon_duck on 2008-01-31
Thanks to both for the help. I'll follow it through.

I'll be in the land of nod in an hour or so. But back on line about 12.00 GMT

---

### Post by lemon_duck on 2008-01-31
I've attached a copy of the Command screen including my error of not reading on before
"gksudo" ntfs-config (unmount the drive before doing this)

I've done this incase there is need for a copy tomorrow.

Many Thanks


dave@dave-desktop:~$ sudo mkdir /mnt/hdb
[sudo] password for dave:
dave@dave-desktop:~$ dave@dave-desktop:~$ sudo mkdir /mnt/hdb
bash: dave@dave-desktop:~$: command not found
dave@dave-desktop:~$ [sudo] password for dave:
bash: [sudo]: command not found
dave@dave-desktop:~$ dave@dave-desktop:~$  sudo mkdir /mnt/hdb
bash: dave@dave-desktop:~$: command not found
dave@dave-desktop:~$  sudo mkdir /mnt/hdb
mkdir: cannot create directory `/mnt/hdb': File exists
dave@dave-desktop:~$ sudo mount /dev/hdb /mnt/hdb
mount: you must specify the filesystem type
dave@dave-desktop:~$ sudo mount /dev/hdb /mnt/hdb/ -t ntfs
[sudo] password for dave:
NTFS signature is missing.
Failed to mount '/dev/hdb': Invalid argument
The device '/dev/hdb' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
dave@dave-desktop:~$ sudo mount /dev/hdb1 /mnt/hdb -t ntfs-3g
dave@dave-desktop:~$ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfsprogs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@dave-desktop:~$ gksudo ntfs-config
dave@dave-desktop:~$ sudo umount /mnt/sdb
[sudo] password for dave:
umount: /mnt/sdb: not found
dave@dave-desktop:~$ sudo umount /dev/sdb1
umount: /dev/sdb1: not found
dave@dave-desktop:~$ sudo umount /dev/hdb
umount: /dev/hdb: not mounted
dave@dave-desktop:~$ gksudo ntfs-config
ntfs-config: command not found
dave@dave-desktop:~$

---

### Post by jan quark on 2008-01-31
sry lemon_duck that the help is such slow this time
but I am not that proficient yet

we will see us tomorrow

---

### Post by Rocket2DMn on 2008-01-31
> dave@dave-desktop:~$ sudo mount /dev/hdb1 /mnt/hdb -t ntfs-3g
dave@dave-desktop:~$ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree
Reading state information... Done
ntfsprogs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Right there you had the partition mounted and when you tried to install ntfsprogs, it said you already have it.  You were in business
If you run that mount command, you will see the drive at /mnt/sdb - maybe you should consider renaming that folder to sdb1 so as not to confuse yourself.

---

### Post by lemon_duck on 2008-02-01
Hello again

I read both responses this a.m. 
 	
I appreciate your assistance jan quark, I learned some time ago that the best way to learn is to teach and if my questions assist you as a 'by product' that's great.

Rocket2DMn suggested renaming sdb to sdb1. So:

I opened the File Browser and Local Disk was immediately visible and accessable. Perhaps at some stage yesterday evening I should have done a 'restart' because from time to time I had used the File Browser expecting it to show Local Disk being available, but it wasn't seen. Nor did I turn off the computer between our various sessions.

But another puzzle is that entering sdb in a search does not find sdb.

I'll review accessing and renaming files via Terminal later today.

In the meantime I have to review the 'bosses' download for her lunchtime viewing.

---

### Post by jan quark on 2008-02-01
> I opened the File Browser and Local Disk was immediately visible and accessable

does this mean you are able to access the files you wanted to ?

I lost the overview a bit...:)

---

### Post by lswest on 2008-02-01
um, about > Rocket2DMn suggested renaming sdb to sdb1, i think he meant you should rename the mount point /mnt/hdb to /mnt/hdb1, since that's the name of the partition actually being mounted there.

---

### Post by lemon_duck on 2008-02-01
> **lswest said:**
> um, about , i think he meant you should rename the mount point /mnt/hdb to /mnt/hdb1, since that's the name of the partition actually being mounted there.

I can understand that. I'll look up the proceedure and try and implement.

Thanks

---

### Post by lemon_duck on 2008-02-01
> **jan quark said:**
> does this mean you are able to access the files you wanted to ?

I lost the overview a bit...:)

Yes the files are easily found now. The next project is to set up a wired connection to the Tablet for fast transfer in both directions.

Many Thanks

---

### Post by jan quark on 2008-02-01
glad to hear

for the wired connection thing

start a new thread, so the things don't miix up

and please mark this thread as solved, if it is solved for you, using the thread tools at the top of the page 
thank you

---

