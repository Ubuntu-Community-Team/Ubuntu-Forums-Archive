---
title: "Linux Swap isn't working."
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by evilbolt on 2007-03-22
Yesterday when I was booting up my ubuntu screen didnt come up and instead it went into Verbose mode and said something was wrong with my boot/swap partition(i think these are the same thing??). I didnt record the error because within a few seconds the screen changed.  I dont think its working now because system monitor  shows 0% use for swap.  How can I fix this?  

Thanks

---

### Post by taurus on 2007-03-22
Can you post the output of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by adieb on 2007-03-22
just because of 0% usage of the swap-partition, it doesn´t mean that it doesn´t work.  try opening 10 firefox windows or tabs and a bunch of other mem-intensive stuff, then take a look at the systemmonitor again.
 what do  

$>          sudo swapoff -a && sudo swapon -a   

say, if you type it into a console?

---

### Post by mcduck on 2007-03-22
Easiest way to check if swap is working is to run 'free -m' and if the swap line shows 0 in all fields then your swap is indeed not working.

---

### Post by evilbolt on 2007-03-22
> **taurus said:**
> Can you post the output of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1      116312    58621153+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2   *      116312      132569     8193150    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/hda3          132569      153224    10410120   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda4          153224      155056      923737+   f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/hda5          153224      155056      923706   82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300090728448 bytes
240 heads, 63 sectors/track, 38764 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       35989   272076808+   7  HPFS/NTFS
/dev/hdb2           35992       38764    20963880    f  W95 Ext'd (LBA)
/dev/hdb5           35992       38455    18627808+   7  HPFS/NTFS
/dev/hdb6           38456       38764     2336008+   b  W95 FAT32
evilbolt@senex:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=6be05d23-c325-4df2-8ed0-ab3a7cc0d696 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=4894df1d-965f-427e-aa9f-5b23f6e2f86e none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1     /media/multimedia    ntfs-3g       defaults,locale=en_US.utf8       0       0

/dev/hda2     /media/windows     ntfs-3g     defaults,locale=en_US.utf8   0    0

/dev/hdb1    /media/edrive     ntfs-3g     defaults,locale=en_US.utf8   0    0

/dev/hdb5     /media/fdrive     ntfs-3g     defaults,locale=en_US.utf8   0    0


> **adieb said:**
> just because of 0% usage of the swap-partition, it doesn´t mean that it doesn´t work.  try opening 10 firefox windows or tabs and a bunch of other mem-intensive stuff, then take a look at the systemmonitor again.
 what do  

$>          sudo swapoff -a && sudo swapon -a   

say, if you type it into a console?



evilbolt@senex:~$ sudo swapoff -a && sudo swapon -a 
swapon: cannot stat /dev/disk/by-uuid/4894df1d-965f-427e-aa9f-5b23f6e2f86e: No such file or directory


> **mcduck said:**
> Easiest way to check if swap is working is to run 'free -m' and if the swap line shows 0 in all fields then your swap is indeed not working.


evilbolt@senex:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           757        659         98          0         21        468
-/+ buffers/cache:        168        588
Swap:            0          0          0



So I guess its really not working :confused:

---

### Post by taurus on 2007-03-23
Edit /etc/fstab from a terminal with

```
gksudo gedit /etc/fstab
```
and remove this line

```
UUID=4894df1d-965f-427e-aa9f-5b23f6e2f86e none swap sw 0 0
```
and replace it with this one.

```
/dev/hda5   none   swap   sw   0   0
```
Save it.  Now, run

```
sudo mount -a
free
```

---

### Post by evilbolt on 2007-03-23
Yay, that worked (after a restart :)    )   . Thanks to all

---

### Post by disturbedite on 2007-03-23
@taurus

i have a somewhat similar problem and the resolution recommended is to use uuid to mount hdds.  its cuz of the recent change with kernel switching from using pata drivers for sata to the (now) default sata drivers.  it renames all (ide) devices to sata devices.  (i.e. hda --> sda).  another reason for that that i also read is that the new default sata drivers are supposed to be better than the ide drivers for both ide & sata devices.  (something to do with stack or stack flow or something like that).
i also have a couple flash drives and that some times causes linux to play musical chairs with my mount points.  (even my hdds).  apparently from what i read, with external devices, like flash drives, it is a lottery in regards to hotplugging your external device(s) and where linux mounts it.  in other words, at least with flash drives, it often doesn't mount them in the last mount point it did before.
i believe changing the drives to mount according to uuid may have disabled my swap too, cuz i get 0's in all those fields as well.

so my question is this:  is there an alternative route i can take to get swap working again instead of changing from uuid with mount points?

---

### Post by mcduck on 2007-03-23
> **disturbedite said:**
> 
so my question is this:  is there an alternative route i can take to get swap working again instead of changing from uuid with mount points?
Yes. You can instead of removing the wrong UUID number change it into correct one.

To get UUID's for your partitions run 'ls -l /dev/disk/by-uuid'. Then check the correct UUID for hda5 and put that in your fstab.

---

### Post by disturbedite on 2007-03-23
ummm....that is what i'm doing...

---

### Post by mcduck on 2007-03-24
> **disturbedite said:**
> ummm....that is what i'm doing...

OK, I suppose I misunderstood what you were trying to say. I believe it's possible to use partition labels instead of UUID or /dev/xxxx-style. But that's not going to work with swap partitions as swap filesystem can't have a label.

Anyway, if you are using correct UUID for your swap it's quite unlikely that using the UUID would be the reason for your swap not working.

---

### Post by KuruOujou on 2008-04-06
This may not work for you, but it's how I got my swap working after foolishly trying to wipe it (not for any reason other than boredom...I gotta get a better hobby)

You could try re-initializing the swap. I'm using /dev/hda2 for my partition, so I ran

```
sudo mkswap /dev/hda2
sudo swapon -a
```

I beileve you would have to put in the device. However, you should only have to run this command once, as mkswap simple initializes the swap by adding a few necessary bytes of data to it, that should never go away.

---

### Post by roboconnell on 2008-04-18
I want to second what mcduck says.  I think removing the UUID and replacing with the device name will work, but I would be worried that it could cause different problem - maybe with hibernate etc. or furture updates.

another way to check the UUID is 

sudo vol_id -u /dev/sda1 (or whatever)

then the string returned should match that in /etc/fstab

I had this same problem, I found the UUID string was wrong in /etc/fstab and this worked for me.  Now why the string ever got to be the wrong value, I'd love to know - maybe an update gone wrong?

---

