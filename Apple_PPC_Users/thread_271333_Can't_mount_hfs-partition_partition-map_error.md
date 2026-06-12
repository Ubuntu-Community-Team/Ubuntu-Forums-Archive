---
title: "Can't mount hfs-partition: partition-map error?"
date: 2006-10-04
forum: Apple PPC Users
---

### Post by emkersyt on 2006-10-04
I hope somebody can help me with this problem I have. During the installation of Ubuntu 6.06 LTS together with OSX 10.3.9 on my powerbook G4 I formatted the "home" of OSX in UFS-Format because I thought it might be a good data-exchange-format between the two systems. Later I found out that this was quiete unnessesary as hfs+ and ext2 also work fine.

So I erased this partiton with "gparted" which did'nt cause problems to any of the systems. 
But then in the next step gparted refused to format hfs+ (just hfs with a max. size of about 2G and others like ext2 etc).

So I tried to create a hfs-partition with "mac-fdisk". This seemed to work at first but now neither OSX nor Ubuntu recognizes this partition any more.

This is what mac-fdisk shows (where /dev/hda5 is the problematic one)

[HTML]/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2         Apple_UNIX_SVR2 swap                  488282 @ 95486072  (238.4M)  Linux swap
/dev/hda3               Apple_HFS Apple_HFS_Untitled_2  32134896 @ 262208    ( 15.3G)  HFS
/dev/hda4              Apple_Boot eXternal booter        17408 @ 32397104  (  8.5M)  Unknown
/dev/hda5               Apple_HFS OSXhome             63071560 @ 32414512  ( 30.1G)  HFS
/dev/hda6         Apple_UNIX_SVR2 linux               15625001 @ 95974354  (  7.5G)  Linux native
/dev/hda7         Apple_UNIX_SVR2 home                44702133 @ 111599355 ( 21.3G)  Linux native
/dev/hda8         Apple_Bootstrap untitled              262144 @ 64        (128.0M)  NewWorld bootblock

Block size=512, Number of Blocks=156301488
DeviceType=0x0, DeviceId=0x0[/HTML]


I tried to mount it but the normal mount -t didn't work:


[HTML]root@kvlarsylix:~# mount -t hfs /dev/hda5 /mnt mount: wrong fs type, bad option, bad superblock on /dev/hda5, missing codepage or other error In some cases useful info is found in syslog - try dmesg | tail or so[/HTML]


Then I found out about this which seems to be the hfs-mount:


[HTML]root@kvlarsylix:~# hmount /dev/hda5 5 hmount: /dev/hda5: invalid partition map (Invalid argument)[/HTML]

So I tried also this


[HTML]root@kvlarsylix:/dev# hformat -l "OSXhome" /dev/hda5 5 hformat: /dev/hda5: invalid partition map (Invalid argument)[/HTML]

because I thought I´d remember that one has got to kind of introduce the new partition to the system.



Don't know really what to do next to get this partition working. Do I have to edit the partition-table somehow? Or should there happen some other process after formatting before mounting it?

---

### Post by kulath on 2006-10-04
I think that neither gparted nor mac-fdisk can actually format a partition in hfs format. I have asked about this in this forum, and I have seen others ask also, but without any answers actually being given.

(By the way, what parameter did you use with mac-disk, because I didn't find any description of what you would use for hfs?)

I think that you may have written some information to the partition map about the partition, but not actually formatted the partition - I don't know whether this is consistent with the symptoms, because I would have thought that Mac OS X would see the partition, and offer to format it for you - but then again perhaps it doesn't.

I think this is also consistent with linux refusing to mount a partition that is not formatted. Not sure about hformat - not heard of that app before, perhaps you just gave the wrong parameters.

I too have been trying to hfs format a partition form with in the alternate installer, but without success. I think you hav eto boot from the Apple install disk,  and format the partition from there (I think you can't format a partition on the current boot disk - hence why you cannot format just by booting into Mac OS X).

---

### Post by emkersyt on 2006-10-05
I opened mac-fdisk with:

mac-fdisk /dev/hda

Then it prompted me for a command. With p it printed out the table and then  I used C (Capital-letter) to create a new partion from the free space. The capital-letter option asks also for the format, so I put HFS there.
As a next step I printed the table again and I saw that it was identical to the other HFS-partition which had been created by the system during the installation. 
Then I saved it and re-opened it and it was just like I had been editing it. So I think this part worked out well but it seems to me that what has not been done properly was the editing of the partition-map.
Maybe you are right that one could't actually format parts of the drive which is currently the boot-disk but as far as I understood it the application mac-fdisk is precisly made for formatting mac-partitions hence  for hfs and maybe even hfs+, isn't it?. (Maybe I'm wrong here and it's just ment to format a partition which was formated already before as hfs.) 
Anyway, I think I gonna try it from another mac with the firewire-mode. If I do it from my own OSX-partition with disk-utility it's going to erase also my system because both partitions actually share the same primary one. (that's at least of what disk-utility is cautioning me about)

---

