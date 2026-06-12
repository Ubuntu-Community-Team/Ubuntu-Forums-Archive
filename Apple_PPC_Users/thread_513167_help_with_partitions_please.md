---
title: "help with partitions please"
date: 2007-07-30
forum: Apple PPC Users
---

### Post by Bikerbob on 2007-07-30
I have a G4 with a 30gig in it.

I have installed OsX 10.3.9 and Os9 each on their own partitions.

I am trying to install Ubuntu on this machine as well.

Now I wish there was an easy way to copy and paste all the partition map to this msg.

The long and the short is.. I need a partition to put Yboot on.

I have partitions setup for swap and / root, but it trys to find the bootstrap partition and I have not made one.. because I assume that linux (Ubuntu) is the OS that requires this partition and not the two Apple systems.

So without trashing everything that I have done can I add the partition now?

Apple puts a tonn of tiny little partitions at the front of the drive. When I view the map in gparted, I see that everthing from hda1 to hda8 is used up in system unknown partitions.
hda 10 is my swap and hda 16 is my /root

I also notice that each Apple Os has a 128mb partition that preceeds it? these are for booting? 

Can I steel some space from my swap partition and use that for a Yboot partiion?

Hope someone can help.

James

---

### Post by pxwpxw on 2007-07-30
Here is what I do, just use mac-fdisk to change a spare 128M partiton to type Apple_Bootstrap
Then select it as boot partition in the partitioning stage.
I have not had any problems from stealing it from Macosx (so far).

```
admax@bigmac:~$ sudo mac-fdisk -l /dev/sda
/dev/sda
        #                    type name                  length   base      ( size )  system
/dev/sda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sda2         Apple_Bootstrap ubootsda              262144 @ 64        (128.0M)  NewWorld bootblock
/dev/sda3               Apple_HFS Apple_HFS_Untitled_1  25126936 @ 262208    ( 12.0G)  HFS
/dev/sda4         Apple_UNIX_SVR2 dbroot              39062501 @ 25389144  ( 18.6G)  Linux native
/dev/sda5         Apple_UNIX_SVR2 swap                 5859376 @ 64451645  (  2.8G)  Linux swap
/dev/sda6         Apple_UNIX_SVR2 uspare              19531251 @ 70311021  (  9.3G)  Linux native
/dev/sda7         Apple_UNIX_SVR2 uxroot2             39062501 @ 89842272  ( 18.6G)  Linux native
/dev/sda8         Apple_UNIX_SVR2 uspare2             27396715 @ 128904773 ( 13.1G)  Linux native

Block size=512, Number of Blocks=156301488
DeviceType=0x0, DeviceId=0x0

admax@bigmac:~$ 
```

---

### Post by Bikerbob on 2007-07-30
Ok this is what I have, A lot of partitions, but I dont have space near the front of the drive??? what should I do?
You are saying to take one of the 128mb partitions.. and does it matter where in the drive listing it is?? aka hda1 or hda14? and then convert it so that it looks like your sda2 correct?

James

ubuntu@ubuntu:~$ sudo mac-fdisk -l /dev/hda
/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2          Apple_Driver43 Macintosh                56 @ 64       ( 28.0k)  Driver 4.3
/dev/hda3          Apple_Driver43 Macintosh                56 @ 120      ( 28.0k)  Driver 4.3
/dev/hda4        Apple_Driver_ATA Macintosh                56 @ 176      ( 28.0k)  Unknown
/dev/hda5        Apple_Driver_ATA Macintosh                56 @ 232      ( 28.0k)  Unknown
/dev/hda6          Apple_FWDriver Macintosh               512 @ 288      (256.0k)  Unknown
/dev/hda7      Apple_Driver_IOKit Macintosh               512 @ 800      (256.0k)  Unknown
/dev/hda8           Apple_Patches Patch Partition         512 @ 1312     (256.0k)  Unknown
/dev/hda9              Apple_Boot eXternal booter       17408 @ 1824     (  8.5M)  Unknown
/dev/hda10        Apple_UNIX_SVR2 swap                1031168 @ 19232    (503.5M)  Linux swap
/dev/hda11                        untitled                  1 @ 60036464 (  0.5k)  Unknown
/dev/hda12              Apple_HFS Apple_HFS_Untitled_3  3227904 @ 1312544  (  1.5G)  HFS
/dev/hda13                        untitled                  1 @ 1050400  (  0.5k)  Unknown
/dev/hda14              Apple_HFS Apple_HFS_Untitled_4 16515072 @ 4802592  (  7.9G)  HFS
/dev/hda15             Apple_Boot eXternal booter       17408 @ 21317664 (  8.5M)  Unknown
/dev/hda16        Apple_UNIX_SVR2 Apple_UFS_Untitled_5 19342080 @ 21335072 (  9.2G)  Linux native
/dev/hda17             Apple_Boot eXternal booter       17408 @ 40677152 (  8.5M)  Unknown
/dev/hda18              Apple_UFS Apple_UFS_Untitled_6 19341904 @ 40694560 (  9.2G)  Unknown
/dev/hda19             Apple_Free Extra                262143 @ 1050401  (128.0M)  Free space
/dev/hda20             Apple_Free Extra                262144 @ 4540448  (128.0M)  Free space
/dev/hda21             Apple_Free Extra                    15 @ 60036465 (  7.5k)  Free space

Block size=512, Number of Blocks=60036480
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 23, type=0x1
2: @ 120 for 36, type=0xffff
3: @ 176 for 21, type=0x701
4: @ 232 for 34, type=0xf8ff

---

### Post by pxwpxw on 2007-07-31
That is a very scary partition list, maybe there are some you dont really need.
I dont know what all those external booter partitions are needed for. 

However the partition numbers are not in address order, so the 128M free ones are fairly low on the drive. You can print ordered by base address in mac-fdisk.

They may get renumbered by the ubuntu installer anyway, I dont know how that might affect the other systems. I think if you nominate one of the 128MB as boot partition in the installer partitioner, it may take care of things. Sometimes I have had to use mac-fdisk to set the partition type to Apple_Bootstrap which is required by the yaboot installer which formats the bootstrap. I have not had any problems from using the 128MB Apple_Free for boots, not so far.
They seem to be some sort of guard space between Apple HFS partitions, purpose unknown to me. Apple_Bootstrap only needs 1MB, but its not a good idea to try to split them.

Be carefull, with all those partitions I cant say what might happen, but I dont know of any limitation.

---

### Post by Bikerbob on 2007-07-31
yeah.. it is scary, thats why I posted the question.

I installed OS X 10.3.9... but with disk utility I created all the partitions that I thought I would need.. for os X os9 and linux... maybe this was the error?

There is nothing on this computer I need to keep.

What is your suggestion if I want to get all three of these OS on the machine?

Thanks

James

---

### Post by pxwpxw on 2007-08-01
Keep a  MacosX system partition (for apple info and maybe firmware updates, and backup, unix utilities), and a Macos9 if you want one. You can delete the rest in the ubuntu installer and use the ubuntu install partitioner to create what  it needs for linux during the install. Dont try to create partitions for linux by using macos utilities. You can leave free space for later if you dont need it now. If you need to reinstall MacosX and Macos9 to tidy it up and reduce partition size, do that first from the macos installers, leave the rest empty, or as one deletable partition  for linux.
If you want write access from linux to a macos partition, it can be macos extended but not  journalled.
Suggestion only.

.

---

### Post by Bikerbob on 2007-08-06
/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k )  Partition map
/dev/hda2          Apple_Driver43 Macintosh                56 @ 64       ( 28.0k )  Driver 4.3
/dev/hda3          Apple_Driver43 Macintosh                56 @ 120      ( 28.0k )  Driver 4.3
/dev/hda4        Apple_Driver_ATA Macintosh                56 @ 176      ( 28.0k )  Unknown
/dev/hda5        Apple_Driver_ATA Macintosh                56 @ 232      ( 28.0k )  Unknown
/dev/hda6          Apple_FWDriver Macintosh               512 @ 288      (256.0k )  Unknown
/dev/hda7      Apple_Driver_IOKit Macintosh               512 @ 800      (256.0k )  Unknown
/dev/hda8           Apple_Patches Patch Partition         512 @ 1312     (256.0k )  Unknown
/dev/hda9         Apple_Bootstrap untitled               1954 @ 1824     (977.0k )  NewWorld bootblock
/dev/hda10        Apple_UNIX_SVR2 untitled           26847657 @ 3778     ( 12.8G )  Linux native
/dev/hda11              Apple_HFS Apple_HFS_Untitled_9  1953280 @ 28066848 (953. 8M)  HFS
/dev/hda12        Apple_UNIX_SVR2 swap                1215413 @ 26851435 (593.5M )  Linux swap
/dev/hda13              Apple_HFS Apple_HFS_Untitled_10 15467008 @ 30282272 (  7 .4G)  HFS
/dev/hda14             Apple_Free Extra                262144 @ 30020128 (128.0M )  Free space
/dev/hda15             Apple_Free Extra              14287200 @ 45749280 (  6.8G )  Free space

Block size=512, Number of Blocks=60036480
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 23, type=0x1
2: @ 120 for 36, type=0xffff
3: @ 176 for 21, type=0x701
4: @ 232 for 34, type=0xf8ff

So this is what I ended up with. Booted OSX cd.. wiped the drive, created 2 partitions , the HFS ones for os9 and osX. Installed osX. Re-booted into Ubuntu LiveCD and installed Ubuntu allowing it to use the freespace. Re-booted and installed 9.2.2 on the smallest HFS partition.
All three are running on my G4/466 DA. I think I might like to resize the linux partition a bit, as 12gig is a bit much I think.. but looking good so far.

Now if I want to change boot default and os's listed I edit Yboot conf. right?

If I wanted to install Yellowdog to take a look at in the other partition it would add it self to the bootstrap right?

thanks for the help.

James

---

### Post by pxwpxw on 2007-08-06
Keep ubuntu and its existing yaboot.conf (make a backup) as the controlling system,
dont let yellowdog mess with the bootstrap at all, dont let it reinstall yaboot. (I dont know yellow dog details, might be OK). 

So long as you have one working linux on the hard disk you can edit its yaboot.conf to boot anything else. You must run "ybin" so that the changes to /etc/yaboot.conf are put into effect on the bootstrap. 
You should have a careful read of the manual for yaboot.conf and ybin and bootstrap.

You can also add options to yaboot.conf for defaults and for first stage booting 
 (for linux(yaboot) macos macosx network cd ....). 
If you want to split the 12.8G linux do it now, but you will need to think about the effect on other existing partition numbers for booting and mounting by /etc/fstab, cant comment further on that, might need fixing yaboot.conf and fstab.

---

