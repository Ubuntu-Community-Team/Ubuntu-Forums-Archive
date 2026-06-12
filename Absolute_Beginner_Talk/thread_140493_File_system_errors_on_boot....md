---
title: "File system errors on boot..."
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-03-06
I just installed OpenBSD in a triple-boot arrangement with Ubuntu & XPee.  Now, when Ubuntu is selected and initializing, I receive the following messages:  

[B]Starting Enterprise Volume Management System    [COLOR=Red]FAILED[/COLOR] 
Mounting Local File Systems    [COLOR=Red]FAILED[/COLOR]  
[/B]
Any ideas on how to fix this?    

BTW: OBSD seems to be working just fine.

---

### Post by halfvolle melk on 2006-03-06
Might be that /etc/fstab isn't right about the type of file system anymore, that OBSD has changed it on the device Ubuntu is trying to mount. You can use:
```
df -T
``` to check which dev uses what filesystem.

---

### Post by Cousindaddy on 2006-03-06
Thanks for the reply.

Here's what I get with ***df -T***

> Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/hda3     ext3    22042900   3080164  17843008  15% /
tmpfs        tmpfs      517944         0    517944   0% /dev/shm
tmpfs        tmpfs      517944     12588    505356   3% /lib/modules/2.6.12-10-386/volatile
/dev/hda1     ntfs    20482840  10413540  10069300  51% /media/hda1

I'm not sure, but everything looks to be in order, doesn't it?

---

### Post by halfvolle melk on 2006-03-06
What I forgot to mention is that **df -T** only tells you about what is mounted. You say you have a triple boot. The output only shows 2 partitions that can boot (AFAIK): hda1 and hda3.

Try this:
```
ls /dev/hd*
```
This is what I get:
/dev/hda  /dev/hda1  /dev/hda2  /dev/hda5  /dev/hdb  /dev/hdd  /dev/hdd1

The ones with number on it are patritions. Maybe your OBSD is on hda2(?). If so, do this:
```
sudo mount /dev/hda2 /mnt/an_existing_dir
```
Without specifying the type of fs, sudo often gets it right. Then do
```
df -T
```
and it should say what type of fs it is. Adjust your /etc/fstab accordingly:
```
sudo gedit /etc/fstab
```

Hope that helps.

---

### Post by Cousindaddy on 2006-03-06
I don't understand this command:
sudo mount /dev/hda2 /mnt/an_existing_dir
Am I supposed to substitute "an_existing_dir" with something else?

BTW, the output of ***ls /dev/hd**** is:

> /dev/hda  /dev/hda1  /dev/hda10  /dev/hda2  /dev/hda3  /dev/hda4  /dev/hda5  /dev/hda6  /dev/hda7  /dev/hda8  /dev/hda9  /dev/hdc  /dev/hdd


---

### Post by halfvolle melk on 2006-03-06
> I don't understand this command:
sudo mount /dev/hda2 /mnt/an_existing_dir
Am I supposed to substitute "an_existing_dir" with something else?
mount works like this:
mount [device/partition] [mountpoint]
[mountpoint] needs to excist for the mount command to work.

So you could make a mount point for instance by doing:
```
sudo mkdir /mnt/my_obsd_partition_or what_have_you
```
Then the above command will translate to (IF hda2 is the partition that failed to mount)
```
sudo mount /dev/hda2 /mnt/my_obsd_partition_or what_have_you
```

> /dev/hda1 /dev/hda10 /dev/hda2 /dev/hda3 /dev/hda4 /dev/hda5 /dev/hda6 /dev/hda7 /dev/hda8 /dev/hda9
Wow, that's a s**tload of partitions. To see what you are trying to mount at start-up do
```
cat /etc/fstab
```
and post it here.

---

### Post by Cousindaddy on 2006-03-06
Here's the output of ***cat /etc/fstab***:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/hda5     ntfs    defaults        0       0
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
 
(BTW: I never could get used to the taste of Karne Melk)

---

### Post by Cousindaddy on 2006-03-06
Here's an excerpt from my sys.log:

> localhost kernel [4294676.589000] bad subpartition - ignored
localhost kernel [4294676.589000] bad subpartition - ignored
localhost kernel [4294676.589000]  >
localhost kernel [4294676.603000] hdc: ATAPI 40X DVD-ROM drive, 512kB Cache
localhost kernel [4294676.603000] Uniform CD-ROM driver Revision: 3.20
localhost kernel [4294676.618000] hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
localhost kernel [4294677.014000] Attempting manual resume
localhost kernel [4294677.014000] swsusp: Suspend partition has wrong signature?

Perhaps Ubuntu & OBSD are fighting over the same swap?

---

### Post by halfvolle melk on 2006-03-06
I think hda5 fails to mount and gives you **FAILED** at boot. I don't get the sys.log. This requires someone that does know what he's talking about. I'm actually just a n00b, sorry.

> (BTW: I never could get used to the taste of Karne Melk)
Hehe, I guess it's an aquired taste ;)

---

