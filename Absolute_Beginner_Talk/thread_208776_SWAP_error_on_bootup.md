---
title: "SWAP error on bootup?"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by bzburr on 2006-07-04
hi my ubuntu takes ages to boot up
dmesg shows
"Unable to handle swap header version 104608"

which i take it to mean the swap partition is the problem?

what can  do to fix it?

Buzz

relevant section of dmesg follows:

[17179593.044000] eth0: Media Link On 100mbps full-duplex 
[17179767.292000] lp0: using parport0 (interrupt-driven).
[17179767.352000] Unable to handle swap header version 104608
[17179767.480000] EXT3 FS on hda1, internal journal
[17179767.664000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179767.664000] md: bitmap version 4.39
[17179768.344000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179770.124000] cdrom: open failed.
[17179770.468000] ext3: No journal on filesystem on hda5
[17179770.476000] Unable to handle swap header version 104608
[17179771.652000] ACPI: Power Button (FF) [PWRF]
[17179771.652000] ACPI: Power Button (CM) [PWRB]
[17179771.652000] ACPI: Sleep Button (CM) [FUTS]
[17179771.764000] ibm_acpi: ec object not found
[17179771.796000] pcc_acpi: loading...
[17179778.032000] ppdev: user-space parallel port driver
[17179778.648000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179778.648000] apm: overridden by ACPI.
[17179782.104000] Bluetooth: Core ver 2.8
[17179782.104000] NET: Registered protocol family 31
[17179782.104000] Bluetooth: HCI device and connection manager initialized
[17179782.104000] Bluetooth: HCI socket layer initialized
[17179782.124000] Bluetooth: L2CAP ver 2.8
[17179782.124000] Bluetooth: L2CAP socket layer initialized
[17179782.128000] Bluetooth: RFCOMM socket layer initialized
[17179782.128000] Bluetooth: RFCOMM TTY layer initialized
[17179782.128000] Bluetooth: RFCOMM ver 1.7
[17180036.764000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17180036.940000] ISOFS: changing to secondary root

---

### Post by richbarna on 2006-07-04
> [17179770.468000] ext3: No journal on filesystem on hda5
[17179770.476000] Unable to handle swap header version 104608

Is the swap partition formatted properly ?

Try this command in the terminal, and post what you see :-
> sudo fdisk -l /dev/hda

---

### Post by bzburr on 2006-07-04
hi the command says:

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Extended
/dev/hda5            2331        2434      835348+  82  Linux swap / Solaris


is that good or bad?

Buzz

---

### Post by richbarna on 2006-07-04
[QUOTE=bzburr]hi the command says:

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Extended
/dev/hda5            2331        2434      835348+  82  Linux swap / Solaris


is that good or bad?

Buzz[/QUOTE]

It looks like you have linux on hda1 (seperate)
And then an extended partition with the swap inside it.

It should look something like this :-
>  Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            [COLOR="RoyalBlue"]2331        2434[/COLOR]      835380+    [COLOR="Red"]83  Linux[/COLOR]
/dev/hda[COLOR="Red"]3[/COLOR]            [COLOR="RoyalBlue"]2331        2434[/COLOR]      835348+  82  Linux swap / Solaris


Basically you should normally have hda 1,2,3 (root,home,swap).
For some reason you created root,extended/ with swap inside it.(the blue show the same start and finish, they should be different)

Are you dual-booting with windows? (no hda3 or hda4)
Could you open Gparted and post a screen shot ?

I'm not sure but I think you need to go for a reinstall, because you have to get rid of the "extended" partition.

---

### Post by richbarna on 2006-07-04
To give you an idea what it should look like, here is a screen shot of my dual-boot with Dapper and Edgy.

Boot/Edgy/Dapper/Swap

You can only have four partitions without using an extended partition, and both distros can use the same swap file.

[ATTACH]12210[/ATTACH]

---

### Post by bzburr on 2006-07-04
yes i am running a dual boot system with windows xp
late for work right now but i can post more data after work :)

Buzz

---

### Post by catlett on 2006-07-04
There is nothing wrong with the formation of your partitons. A logical partition has to be inside of an extended partition. The numbers correspond because the extended isn't seperate, it is the same. You could have more than one in the extended and they wouldn't end at the same place.
Linux doesn't care about primary partitions. It will install on a logical just fine.
You know your partitions are fine because they are different numbers. hda2 and hda5.
The 4 primary partitions have the numbers hda1,hda2,hda3 and hda4 reserved for them. Logical partitions start at hda5 and go upward.
You have 2 primaries hda1 and hda2. hda2 is extended and inside it is a logical partition hda5.

[> 17179770.468000] ext3: No journal on filesystem on hda5
That is the questionable line to me. Your system sees hda5 as swap /dev/hda5 > 2331 2434 835348+ 82 Linux [COLOR="Red"]swap / Solaris[/COLOR]
 But at boot your system is loking for an ext3 >  [COLOR="Red"]ext3:[/COLOR] No journal on filesystem on hda5 This makes me wonder if your /etc/fstab is labeling hda5 wrong. Post the out put of this command. It will open a text file in a text edotir ```
sudo gedit /etc/fstab
```

P.S/ FYI... You can only have 4 primaries but many logical partitions. Here is a screenshot of my hard drive. I am just in the process of switching out my other systems so I have lots of empty partitions about to be filled in. It's just so you get an idea about an extended partition with logicals inside of it.

---

### Post by bzburr on 2006-07-07
HI there :)

here is the output (thanks so much for your knowledge and help)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /media/hda5     ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Buzz

---

### Post by richbarna on 2006-07-07
> **catlett said:**
> There is nothing wrong with the formation of your partitons. A logical partition has to be inside of an extended partition. 

Why the extended partition? He can have upto 4 partitions without it.
hda1 boot
hda2 ext3
hda3 swap

Also:-
Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux

/dev/hda2            2331        2434      835380    5  Extended
/dev/hda5            2331        2434      835348+  82  Linux swap / Solaris

To me that makes no sense, if you are dual booting with windows, I take it that windows is on another drive as this is only 20 Gig.

---

### Post by bzburr on 2006-07-07
yes windoze is on the 200 g HD, Ubuntu on the 20 gig HD
 other than that i dont care how many partitions , and would love to know how to fix the boot problem
cheers :)
Buzz

---

### Post by catlett on 2006-07-08
I have found your error!
This is the problem. In your /etc/fstab, hda5 is listed twice


```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
[COLOR="Red"]/dev/hda5 /media/hda5 ext3 defaults 0 2[/COLOR]
[COLOR="Red"]/dev/hda5 none swap sw 0 0[/COLOR]
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
```
Just delete this entry ```
[COLOR="Red"]/dev/hda5 /media/hda5 ext3 defaults 0 2[/COLOR]
```
And leave your /etc/fstab looking like this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

``` To open /etc/fstab in a text editor enter this command ```
sudo gedit /etc/fstab
```
Just delete the first /dev/hda5 entry and save the document. Then close and that should be it. With the 2 entries your system was getting confused. It would have mounted hda5 to /media/hda5 because that was first and it would get the error when trying to mount hda5 as swap. Second, mounting hda5 as ext3 would give an error because it is formatted as swap.

Anyways just edit /etc/fstab and you should be fine.

P.S. There is nothing wrong with having logical partitions. And your partitions do not have to be next to each other. Years ago booting to certain parts of a drive was an issue but not with newer computers. Years ago virtual memory (i,e. swap) was more vital and putting the swap partition close to root was suppose to help with speed because the needle wouldn't  travel as far between root and swap etc. But again with modern systems and their large amounts of ram, swap isn't accessed that much and hard drives are alot faster.
Your only issue is the double entry for hda5 in /etc/fstab, nothing else is wrong. Any changes you make to your hard drive need only be made if you had a personal preference, your drive isn't partitioned incorrectly.

---

### Post by richbarna on 2006-07-08
> **bzburr said:**
> yes windoze is on the 200 g HD, Ubuntu on the 20 gig HD
 other than that i dont care how many partitions , and would love to know how to fix the boot problem
cheers :)
Buzz
I would just reinstall ubuntu on the 20 gig from scratch, using three partitions.
p1 Boot (1Gb)   ext3, 
p2 Root (18Gb) ext3 
p3 Swap (1Gb)  Linux-Swap

Nice and simple and without the "extended" partition. Everybody has their way of doing things, I can only show you how I would do it.

EDIT: Do what catlett said, he should know, he is the king of partitioning :)
         You only have to look at his screen shot.
PS: Hey Catlett, that is some damn fine partitioning you've got there !!!! How many different distros have you got crammed into that drive ?

---

### Post by bzburr on 2006-07-11
:( it didnt help 

it still pauses for ages then fails and ubuntu eventually loads up

but no change in speed
Buzz

---

### Post by mcmillan on 2006-07-28
I'm kind of taking a stab here, but since you had an error in your fstab file listing the same partition as two different types, I'm wondering if the partition my have the wrong file system on it. You want it to be as swap, but there was originally listed as both swap and ext3. If it's actually formatted as ext3 it may cause problems trying to boot it as swap after you delete the problamatic line in fstab. Maybe try booting with a liveCD so you can reformat as swap.

---

