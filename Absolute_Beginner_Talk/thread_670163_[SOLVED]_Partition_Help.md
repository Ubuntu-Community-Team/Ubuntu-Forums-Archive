---
title: "[SOLVED] Partition Help"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by tad1073 on 2008-01-17
Quote:
Originally Posted by tad1073 View Post
@ wieman01:

Do you think you could give me a hand also. I am not dual booting but I have 3x9.1gb hd's w/ubuntu on sda ext3 on sda1 and swap on sda5, sdb is unformated and sdc is unformated, sdc1 is ext3 and sdc5 is swap. I tried to do a manual partition from the live cd but I didn't know enough about partitioning and didn't have all the info I needed.
No problem. Just open up a new thread and send me the link by PM.

I have to carry my ubuntu box down stairs so I can have internet access on it. We have a  wireless router but no cat5 run to other parts of the house and I couldn't get the wireless card (that i bought then returned) to work.

---

### Post by Sef on 2008-01-17
> Do you think you could give me a hand also. I am not dual booting but I have 3x9.1gb hd's w/ubuntu on sda ext3 on sda1 and swap on sda5, sdb is unformated and sdc is unformated, sdc1 is ext3 and sdc5 is swap

To make sure I understand, 3 have hard drives of 9.1 gigabytes each.  Let's just deal with sda.  I would make a 8 gb partition and make that root (/).   The other 1.1 gb,  I would make a swap partition.  

First I would keep 'Use As' as ext3, and then set mount point as / (root); then set the partition for 8 gb, and turn the bootable flag to on (use the space bar once you highlight that.)  Next I would the remaining 1.1 gb as swap - just highlight 'Use As', enter, then highlight swap.  

If you want a home partition, then I would repeat the process with sdb or sdc, and use the same file system; however, instead of /, I would highlight 'Mount Point', enter, and highlight home.

---

### Post by tad1073 on 2008-01-17
let me get blkid and fdisk info put on disk and will post it.

---

### Post by tad1073 on 2008-01-17
couldn't get fdisk to work for me so I wrote the info down that gparted was showing.

/dev/sda1 ext3  8.07gb  2.94gb used  5.12gb unused
      /sda2 extended 415.74mb
      /sda5 swap 415.71mb

/dev/sdb1 unknown 8.08gb
       /sdb2 extented 415.74mb
      /sdb5 swap 415.71mb

/dev/sdc1 unknown 8.07gb

/dev/sda1: UUID="972eb4ae-1316-48c0-ac79-6c5dad0c3ff9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="26258792-344f-4de6-8ad1-bc50580d1e8a" TYPE="swap" 
/dev/sdb5: UUID="bccb585b-ead7-438b-bcaa-d02b2aaf7c1c" TYPE="swap" 

how do I get the UUID for sdc1

Disk /dev/sda: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00079d3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1053     8458191   83  Linux
/dev/sda2            1054        1106      425722+   5  Extended
/dev/sda5            1054        1106      425691   82  Linux swap / Solaris

Disk /dev/sdb: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1203

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1053     8458191   83  Linux
/dev/sdb2            1054        1106      425722+   5  Extended
/dev/sdb5            1054        1106      425691   82  Linux swap / Solaris

Disk /dev/sdc: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000eb9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1106     8883913+   5  Extended

took the book flag off of sdb1 now my system will not boot help!!!

---

### Post by tad1073 on 2008-01-17
bump- need some help

---

### Post by tad1073 on 2008-01-17
never mind I fixed it, But how can I unmount the main volume so i can increase the swap to 1gb

---

### Post by wieman01 on 2008-01-18
> **tad1073 said:**
> never mind I fixed it, But how can I unmount the main volume so i can increase the swap to 1gb
You will have to boot from the Live CD in order to do so. It's a fairly simple process if you use GParted. If you need further help, just post here.

---

### Post by tad1073 on 2008-01-18
I need to change the access of the other drives. As of now everytime I mount them I have to enter my password, I  want to use them as extra space because my drives are only 9.1 gb. Also, does sda2 extended have to be wrapped around sda5 swap and the same for sdb2 and sdb5? What would I have to do tho put the swap space on sdc5 and not have swap on sda5 and sdb5

---

### Post by wieman01 on 2008-01-18
You would have to format "/dev/sdc5" accordingly and have to edit:
> sudo gedit /etc/fstab
Post the contents and I'll show you what you have to change. It should be simply.

---

### Post by tad1073 on 2008-01-18
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=972eb4ae-1316-48c0-ac79-6c5dad0c3ff9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=26258792-344f-4de6-8ad1-bc50580d1e8a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

I don't know the command to pull the above info from sdb and sdc, but I wrote down some info from properties.

/media/disk/ ext2 UUID=f9c5b947-6eea-43ab-aa36-9cc2e9cfd673 rw nosuid nodev

/media/disk2 ext2 UUID=06686ac4-0e0d-4816-8340-223f026aedfa rw nosuid nodev

Basicly I want thethree drives to act like one.

Off topic:

About a week ago I bout a D-Link Extreme N Desktop wireless card (this was when I was running a coy of xp) i put it in myself and it worked fine with xp. So i uninstalled xp installed ubuntu (for the fifth time), did lspci and the card was recognized as being in the slot.

ubuntu@ubuntu:~$ sudo lshw -C network
*-network
description: Ethernet interface
product: 82557/8/9 Ethernet Pro 100
vendor: Intel Corporation
physical id: 5
bus info: pci@0000:01:05.0
logical name: eth0
version: 08
serial: 00:50:8b:9a:ab:3a
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

*-network UNCLAIMED
description: Network controller
product: AR5416 802.11a/b/g/n Wireless PCI Adapter
vendor: Atheros Communications, Inc.
physical id: 3
bus info: pci@0000:00:03.0
version: 01
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list
configuration: latency=64
ubuntu@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.


Installed ndisgtk and ndis wrapper, installed net5416.inf, returned invalid driver. I didn't know where to put ar5416.sys, so I returned the card to best buy

I installed madwifi but i am totally clueless on how to use it and if the drivers come with the program or if I have to put the drivers in myself and if I have to put the drivers in myself, where.

---

### Post by wieman01 on 2008-01-18
**Tad:**

Are you sure you want to have your SWAP partition on an external drive? That is somehow unusual and I would rather refrain from it... Why not extend the current SWAP disk by utilizing space from the partition to the left of it?

---

### Post by tad1073 on 2008-01-18
Those drives aren't external, I guess that is what ext3 means huh? What do I need to remormat them to so they will be recognized as internal. I have already extended the swap that is on sda5 to 2gb, so that will work for me, just need to know what to reformat the other two drives to.

---

### Post by wieman01 on 2008-01-18
> **tad1073 said:**
> Those drives aren't external, I guess that is what ext3 means huh? What do I need to remormat them to so they will be recognized as internal. I have already extended the swap that is on sda5 to 2gb, so that will work for me, just need to know what to reformat the other two drives to.
"ext3" is actually the file format of your regular Linux partition. It's like NTFS for Windows.

You have resized 'sda5' to 2 GB, so why do you want to move SWAP to any other driver then? 2 GB should really do, use the other drives as data / backup volume, how about that?

---

### Post by tad1073 on 2008-01-18
Yeah, i just want to use them as extra stroage and not have to enter my password everytime i access them. More or less I want them to be an extension of the main drive.

---

### Post by wieman01 on 2008-01-18
> **tad1073 said:**
> Yeah, i just want to use them as extra stroage and not have to enter my password everytime i access them. More or less I want them to be an extension of the main drive.
That's an entirely different story then. The right FS format will be "ext3" and not SWAP. Can you mount the volume right now? If so, how do you do it?

You want to have access to these drives without having to mount them, is that correct?

---

### Post by tad1073 on 2008-01-18
Yeah, I can mount them, I just have to enter my password every time I do and I don't have write access to them, or ownership. Right now the owner of the drives are root and they are read only. I want to be the owner of the drives and have read write access to them.

---

### Post by wieman01 on 2008-01-19
> **tad1073 said:**
> Yeah, I can mount them, I just have to enter my password every time I do and I don't have write access to them, or ownership. Right now the owner of the drives are root and they are read only. I want to be the owner of the drives and have read write access to them.
Ok, we need to mount the volumes upon boot then and give your user the right to access them. No problem.

Before we begin, is there a chance that you format these 2 drives to 'ext3' instead of 'ext2'? It's currently a 'ext2' file system which isn't as up-to-date.

---

### Post by wieman01 on 2008-01-19
Please make a safety copy of "/etc/fstab" first:
> sudo cp /etc/fstab /etc/fstab_backup
Create mount point:
> sudo mkdir /mnt/sdc5
Now open "/etc/fstab":
> sudo gedit /etc/fstab
Now add this line at the very end of the file:
> # /dev/sdc5
/dev/sdc5      /mnt/sdc5           ext3    defaults        0       2
When you reboot now, can you see the drive "/mnt/sdc5" here? What does this yield:
> sudo fdisk -l

_**EDIT:**_
You might now yet have write access to the disk, but let's tackle that later:
> sudo chown your_user:your_user /mnt/sdc5

---

### Post by tad1073 on 2008-01-19
fdisk results:

Disk /dev/sda: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00079d3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         845     6787431   83  Linux
/dev/sda2             846        1106     2096482+   5  Extended
/dev/sda5             846        1106     2096451   82  Linux swap / Solaris

Disk /dev/sdb: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1203

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1106     8883913+  83  Linux

Disk /dev/sdc: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000eb9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1106     8883913+  83  Linux

I did 
```
sudo chown my user name:my user name /mnt/sdb1 
"                                         "                     " /mnt/sdc1
```
now when I try to mount the drives I get an error that says you are not priviledged to mount this volume.

---

### Post by wieman01 on 2008-01-19
Ok, let's start all over again... Which device are we talking about right now? And what does "/etc/fstab" look like?

---

### Post by tad1073 on 2008-01-19
the error message only appears when I try to mount the volume from the disk icon, but when i go into /mnt/sdb1 or sdc1 and check permission from the properties tab it shows that I am the owner and am able to create and delete files from there.

Thanks for all your help, I rally do appreciate it.

Do you think you can give me a hand with the wifi problem I encountered. i have contacted source forge but they have not given me an answer to my question.

About a week ago I bout a D-Link Extreme N Desktop wireless card (this was when I was running a coy of xp) i put it in myself and it worked fine with xp. So i uninstalled xp installed ubuntu (for the fifth time), did lspci and the card was recognized as being in the slot.

ubuntu@ubuntu:~$ sudo lshw -C network
*-network
description: Ethernet interface
product: 82557/8/9 Ethernet Pro 100
vendor: Intel Corporation
physical id: 5
bus info: pci@0000:01:05.0
logical name: eth0
version: 08
serial: 00:50:8b:9a:ab:3a
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

*-network UNCLAIMED
description: Network controller
product: AR5416 802.11a/b/g/n Wireless PCI Adapter
vendor: Atheros Communications, Inc.
physical id: 3
bus info: pci@0000:00:03.0
version: 01
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list
configuration: latency=64
ubuntu@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.


Installed ndisgtk and ndis wrapper, installed net5416.inf, returned invalid driver. I didn't know where to put ar5416.sys, so I returned the card to best buy

I installed madwifi but i am totally clueless on how to use it and if the drivers come with the program or if I have to put the drivers in myself and if I have to put the drivers in myself, where. They mention the ar5416 chipset with the dwa-547 but they don't mention the dwa-552 which has the same chipset, any ideas?

---

### Post by wieman01 on 2008-01-19
Before we go ahead and tackle your wireless issues, can you now access your hard drives? No other issue with them? And are they mounted upon boot? That's what I was trying to achieve.

---

### Post by tad1073 on 2008-01-19
Yes they are mounted at boot. How can I get the icons that are in Computer to coincide with /mnt/sdb1 and sdb2?

---

### Post by wieman01 on 2008-01-19
I just though "/dev/sdc5" we were talking about, hence my confusion.

I don't use Gnome so I don't know how to help you from here, but I imagine you could just delete those icons and create new ones? I think these icons are just like bookmarks that you can edit, delete, and create.

If this issue is closed, do you want to move on?

---

### Post by tad1073 on 2008-01-19
I just noticed that /mnt/sdb1 and /mnt/sdc1 are just monut points for the main drive and not the drives that need to be mounted. I checked the volume and they are showing only 3.2gb available which is the amount left on the main drive.

Disk /dev/sda: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00079d3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         845     6787431   83  Linux
/dev/sda2             846        1106     2096482+   5  Extended
/dev/sda5             846        1106     2096451   82  Linux swap / Solaris

Disk /dev/sdb: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1203

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1106     8883913+  83  Linux

Disk /dev/sdc: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000eb9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1106     8883913+  83  Linux

---

### Post by wieman01 on 2008-01-20
Ok, then I need to ask you to post:
> sudo cat /etc/fstab
> sudo fdisk -l
And please point out once again which hard drive you like to have mounted at boot. Just so that I get it right this time. :-)

---

### Post by tad1073 on 2008-01-20
After I realized that scb1 and sdc1 were just alternate mount points for sda1, I took it upon myself to add the UUID'/ for sdb1 and sdc1 but that didn,t change anyting.

thomas@computer:~$ sudo cat /etc/fstab
[sudo] password for thomas:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=972eb4ae-1316-48c0-ac79-6c5dad0c3ff9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=26258792-344f-4de6-8ad1-bc50580d1e8a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

# /dev/sdb1
UUID=56336294-b24a-4d94-902e-067e43346476
/dev/sdb1 /mnt/sdb1 ext3 default 0 2

# /dev/sdc1
UUID=19ad8331-c5d4-4252-a8c7-693678e35fd1
/dev/sdc1  /mnt/sdc1 ext3 default 0 2


thomas@computer:~$ sudo fdisk -l

Disk /dev/sda: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00079d3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         845     6787431   83  Linux
/dev/sda2             846        1106     2096482+   5  Extended
/dev/sda5             846        1106     2096451   82  Linux swap / Solaris

Disk /dev/sdb: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1203

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1106     8883913+  83  Linux

Disk /dev/sdc: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000eb9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1106     8883913+  83  Linux

---

### Post by wieman01 on 2008-01-20
Tad:

Can you now access...

/mnt/sdb1
/mnt/sdc1

...and are these the right drives? If these drives are there and mapped, please do:
> sudo chown thomas:thomas -R /mnt/sdb1
> sudo chown thomas:thomas -R /mnt/sdc1
These folders should now belong to to your user.

If the folders are missing, please do:
> sudo mkdir /mnt/sdb1
> sudo mkdir /mnt/sdc1

---

### Post by tad1073 on 2008-01-20
> Can you now access...

/mnt/sdb1
/mnt/sdc1

...and ae these the right drives? If these drives are there and mapped, please do:

I can access sdb1 and sdc1 but they are not the right drives, they are just other access points for sda1. There should be about 9gb+/- for sdb1 and sdc1 but both are showing only 3.2gb which is the amount available for sda1.

I got my wireless working btw.

---

### Post by wieman01 on 2008-01-20
Tad:

Just spotted something that we need to correct. Please update 'fstab' so that it reads:
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=972eb4ae-1316-48c0-ac79-6c5dad0c3ff9 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=26258792-344f-4de6-8ad1-bc50580d1e8a none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
[COLOR="Red"]
# /dev/sdb1
/dev/sdb1 /mnt/sdb1 ext3 default 0 2

# /dev/sdc1
/dev/sdc1 /mnt/sdc1 ext3 default 0 2[/COLOR]
I have deleted 2 lines (UID) which might have caused an error. Please restart the PC and see if the right drives have been mounted.

---

### Post by tad1073 on 2008-01-20
i removed the uuid from the entries but the volume is still only showing 3.3gb which is the amount of sda1, i beleive we just created alternate mount points for sda1.

---

### Post by wieman01 on 2008-01-21
> **tad1073 said:**
> i removed the uuid from the entries but the volume is still only showing 3.3gb which is the amount of sda1, i beleive we just created alternate mount points for sda1.
Hi Tad, 

Would it be possible for you to attach a screenshot of GParted for each hard disk that you have? I think that will make it a lot easier for me to give you an advice that makes actually sense. :-) Could you do that?

---

### Post by tad1073 on 2008-01-21
Here are those screen shots.

---

### Post by wieman01 on 2008-01-21
Looks fine. Now what happens when you do:
> sudo mkdir /mnt/sdb1
> sudo mount /dev/sdb1 /mnt/sdb1
> sudo mkdir /mnt/sdc1
> sudo mount /dev/sdc1 /mnt/sdb1
Can you now access these drives?

---

### Post by tad1073 on 2008-01-21
Ok, I am able to mount them and they have the right amount of disk space but the owner of the disks are root again do I need to sudo chown them again, while they are mounted.

---

### Post by wieman01 on 2008-01-21
> **tad1073 said:**
> Ok, I am able to mount them and they have the right amount of disk space but the owner of the disks are root again do I need to sudo chown them again, while they are mounted.
It's ok then. Now we need to work on the automount issue.

There is another type in your 'fstab':
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=972eb4ae-1316-48c0-ac79-6c5dad0c3ff9 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=26258792-344f-4de6-8ad1-bc50580d1e8a none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0

# /dev/sdb1
/dev/sdb1 /mnt/sdb1 ext3 [COLOR="Blue"]defaults [/COLOR]0 2

# /dev/sdc1
/dev/sdc1 /mnt/sdc1 ext3 [COLOR="Blue"]defaults [/COLOR]0 2
It should read 'defaults', not 'default'. Please change it and restart the PC. Any success?

This is a good reference by the way:

[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by tad1073 on 2008-01-21
everyting is good but they don't mount at start up, I think I can live with that though. Thanks for all your help. you are a fountain of knowledge.

---

### Post by tad1073 on 2008-01-21
my desktop if you are interested.

---

### Post by wieman01 on 2008-01-21
> **tad1073 said:**
> everyting is good but they don't mount at start up, I think I can live with that though. Thanks for all your help. you are a fountain of knowledge.
No problem, buddy. It's too bad it does not work at start up, but it is impossible from here to tell what the issue is. But you should know the basics by now :-) so I am sure you can tackle it. Nice talking to you.

---

### Post by tad1073 on 2008-01-21
Yeah, I have a better understanding now. 

]

---

### Post by tad1073 on 2008-01-21
I lied, the hd's are mounted at start up.

---

### Post by wieman01 on 2008-01-22
> **tad1073 said:**
> I lied, the hd's are mounted at start up.
Good, glad to hear it. It makes sense now. :-)

---

### Post by tad1073 on 2008-01-22
Swap is not mounting at start-up now or maybe I just noticed it. sda2 has swap in it.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=972eb4ae-1316-48c0-ac79-6c5dad0c3ff9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=26258792-344f-4de6-8ad1-bc50580d1e8a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

# /dev/sdb1
/dev/sdb1 /mnt/sdb1 ext3 defaults 0 2

# /dev/sdc1
/dev/sdc1  /mnt/sdc1 ext3 defaults 0 2
```

Again, I can't thank you enough for your help. Do you know of anyone that wants to buy a Compaq Smart Array 431 controller. I disabled the array and removed the controller board. i would be willing to trade for 512 pc133 ecc sdram dimm 168 pin if you know of anyone.

You must be a night owl or live in another country or an early riser.

---

### Post by wieman01 on 2008-01-22
Hey Tad, 

No problem, I am an early bird. :-)

Thing is SWAP should not mount in a way you would notice it. SWAP is...
> Swap space is a portion of a hard disk drive (HDD) that is used for virtual memory. 
Definition taken from [here]("http://www.linfo.org/swap_space.html").

So if '/dev/sdb1' and '/dev/sdc1' mount with read and right access, then you are fine. You should not have access to your SWAP partition anyway, as it is only used the kernel and thus the system.

Does that make sense? I take it '/dev/sdb1' and '/dev/sdc1' work fine.

---

### Post by tad1073 on 2008-01-22
you are correct about sdb1 and sdc1.

---

### Post by wieman01 on 2008-01-22
> **tad1073 said:**
> you are correct about sdb1 and sdc1.
That said, please see the other part of my response. SWAP is a partition which extends your RAM, therefore it is not accessible. Your system should be OK now.

---

### Post by tad1073 on 2008-01-22
i installed conky which shows swap usage which there was nothing happening there. So, I check gparted and swap was not on. i had to physically turn swap on from gparted. swap is inside of sda2, could that be the reason it is not coming on at boot?

---

### Post by tad1073 on 2008-04-25
I am back to square one. I did a fresh install of 7.10 and by mistake I created the mount point for sdc1 as media so I changed the mount point in fstab to /sdc1 the drive isn't anywhere to found.

```
:~$ sudo cat /etc/fstab
[sudo] password for thomas: 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c39b7fd3-8030-43e6-801b-4d6e517db65d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=aef133ab-8491-4fa7-885d-e265b0eb4428 /home           ext3    defaults        0       2
# /dev/sdc1
UUID=0627eb73-1e93-4d49-9cbf-fb9f53125a08 /sdc1          ext3    defaults        0       2
# /dev/sda1
UUID=a90836c0-e6a6-4764-80fb-8372f0e4ad44 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
:~$ sudo fdisk -l

Disk /dev/sda: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00079d3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         249     2000061   82  Linux swap / Solaris
/dev/sda2   *         250        1106     6883852+  83  Linux

Disk /dev/sdb: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1203

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1106     8883913+  83  Linux

Disk /dev/sdc: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000eb9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1106     8883913+  83  Linux
 

```

---

