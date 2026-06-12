---
title: "Need help/ Info on mounting drives"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by thedon_1 on 2008-01-18
Hi, i'm running a dual boot system with Ubuntu and Vista on seperate partitions and then a really big NTFS partition for my files that both OS can use.

The thing is i have tried a few Media players and when i try to build collections e.t.c it only shows folders and stuff on the Ubuntu file system and i can't select the NTFS partition (but i can view and access files through computer and then double clicking the drive).

I have been doing some research and have read about mounting the drive. Do i have to mount the drive for this to work? What exactly is mounting the drive? How do i know if it's already mounted e.t.c

Thanks

---

### Post by OldGrey on 2008-01-18
Hi if you can access the files on the NTFS partition in Ubuntu it sounds like it is been mounted automatically.

---

### Post by thedon_1 on 2008-01-18
hmm, so any idea's on how i can get it into the file viewer of Amarok?

Are other partitions viewable through a sub section? 

Also, i have been reading about locations the partitions are mounted to. Could anyone explain this a bit to me please, how does this work, and what does mounting actually mean?

---

### Post by OldGrey on 2008-01-18
Sorry not an Amarok expert. For more info re mounting NTFS (Windows) drives have a look at:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by quarkhirad on 2008-01-18
Dear thedon_1

Hi can you please copy and paste the output of the following commands. 

( open the apllication called terminal from applications menu then accessories you should get something like this )

all@webbi:~$

Offcourse all will be replaced by you username  and webbi by your host name 
 
Then type mount and then press enter

(it should look like this in your screen) 

all@webbi:~$ mount

after typing mount whatever you see just mark it then right click and then click copy and then paste it as a post 


then also type the following 

all@webbi:~$ cat /etc/fstab

please paste the output of this also in the post 

Thanks 

ok also you could check out the following thread . Hope it helps 

[http://ubuntuforums.org/showthread.php?t=310590](http://ubuntuforums.org/showthread.php?t=310590)

Khirad

---

### Post by thedon_1 on 2008-01-18
I'm at work now but i will e home in a few hours and will post the results then, thanks for repying

---

### Post by thedon_1 on 2008-01-18
Ok, here's what i get from mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)



and here is fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d2f9534b-47ae-4def-8644-ce796c54f0f8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d682287b-b981-4e06-9331-757e11fc1761 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0





I manaually added some folder into Amarok and then when i restarted my computer and tried to play those same files in Amarok it didn't let me untill i double clicked on the NTFS partition they are saved on, and then it appeared on the desktop.

---

### Post by thedon_1 on 2008-01-18
Ok so when i riight click on my ntfs drive that my files are on and go to drive, then settings, mount point, file system and mount options are blank.

Am i right in assuming i need to set a mount point?

What is the best way to do this? That's if that's even what i need to do

---

### Post by hyper_ch on 2008-01-18
pls post:

```

sudo fdisk -l

```

```

df -l

```

And amarok has problems with read-only files which would be the case if you didn't use ntfs-3g to mount the ntfs drive. At least it had problems with that back in dapper and edgy.

---

### Post by thedon_1 on 2008-01-18
here is fdisk

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcff3aaff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            7079       28208   169726725    7  HPFS/NTFS
/dev/sda2   *           1        7078    56854003+   7  HPFS/NTFS
/dev/sda3           28209       30238    16299360   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4           30238       30401     1315440    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5           30238       30401     1315408+  82  Linux swap / Solaris

Partition table entries are not in disk order


here is df -l

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             16042780   3057668  12333140  20% /
varrun                  517248        88    517160   1% /var/run
varlock                 517248         0    517248   0% /var/lock
udev                    517248        68    517180   1% /dev
devshm                  517248         0    517248   0% /dev/shm
lrm                     517248     34696    482552   7% /lib/modules/2.6.22-14-generic/volatile

---

### Post by quarkhirad on 2008-01-18
dear thedon_1

Ok now first thing first. I suppose you have only one windows partition and that is your c drive of windows? am i right?

Now open amarok then click on browse to find your songs then click on browse then go to the the root folder ( / folder ) then go to media folder in root and then go to folder called disk and there you go you should see your folders that you made in your c drive in windows. 

If you dint understand or have any trouble tell me i shall try and help. 

Cheers 

Khirad

---

### Post by thedon_1 on 2008-01-18
nice one mate, it's there, only 1 problem though.

It will add files to my Amarok main window and i can play them, it's all good, but when i restart, untill i have double clicked on the partition in computer and it come up on the desktop, it says not found.

---

### Post by quarkhirad on 2008-01-18
YEAH :guitar::guitar::guitar::guitar:


Ok now for your small problem. I have a hunch on what could it be. However, before that i need to know which ubuntu are u using. I.E. is it 6.06 or 6.10 or 7.06 or 7.10.  Also sorry mate as i have to do some testing work at college i uninstalled ubuntu and installed fedora. Hence i shall check out with my friends and then see if i can find out some solution. hence it may take some time. 


Also after restarting you comp. Without doing anything. open terminal and then type mount in the promt and paste the output as a post. 


Till then all the best and i think well you will just have to do with the problem  :(  :(

---

