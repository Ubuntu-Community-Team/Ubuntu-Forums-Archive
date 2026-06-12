---
title: "Dual boot Snow Leopard &amp; 10.04LTS, no more boot into Ubuntu"
date: 2010-06-28
forum: Apple Hardware Users
---

### Post by life_form on 2010-06-28
Hello wise people,

I"m still fairly new to Ubuntu, so, please be patient.

I have a MacBookPro2,2 with Snow Leopard and (until yesterday) Ubuntu 9.10 installed in a dual boot configuration,. I followed this to the T [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu") to install 9.10 and everything worked just great! Yesterday I decided to choose to upgrade 9.10 to 10.04 over the internet, using System > Administration > Update Manager. It took a while until I was asked to shut down the computer. As instructed, I shutdown the computer (no reboot).

After that, I still get the rEFIt dialogue to choose between OSX and Linux. OS X still boots fine. Clicking the penguin, however, results in Linux not loading. My feeling is that Grub (2?) needs to be convinced to do the right thing?

Maybe one or some of you can help me resolve this. I thoroughly enjoy Linux and would like to work with it again (and have fun, too, of course).

Thank you lots in advance.

---

### Post by Helios747 on 2010-06-28
It's been awhile since I've used rEFIt, but try using the partitioning tool withing rEFIt to resync the MBR.


if that doesn't work, as a temporary work around until somebody can give you a solid answer, when you boot up your mac, hold down the "alt" key, two hard drives will pop up, OS X, and "windows" (ubuntu), select "windows".

---

### Post by life_form on 2010-06-28
Hello Helios747,

Thanks-a-bunch for your message. I've re-synched the MBR. When booting now from cold start and choosing to boot Linux I get the following mesage:

GRUB loading
error: the symbol 'grub_puts_' not found
grub rescue>

Any clue as to what this points toward?

I must admit I haven't got one.

---

### Post by linuxopjemac on 2010-06-29
You have to do something about Grub.
Try the rescue methods as described [here ]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")(from liveCD).

---

### Post by life_form on 2010-06-29
Thank you very much, linuxopjemac:

I will give it a shot. Once done, I will report back.

Stay well!

---

### Post by life_form on 2010-07-01
Ok linuxopjemac,

here's what I've done:

ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26       54538   437863836   af  HFS / HFS+
/dev/sda3   *       54538       54538         977    b  W95 FAT32
/dev/sda4           54538       60540    48212891   83  Linux

Disk /dev/sdb: 1 MB, 1048576 bytes
1 heads, 2 sectors/track, 1024 cylinders
Units = cylinders of 2 * 512 = 1024 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 4109 MB, 4109369344 bytes
255 heads, 63 sectors/track, 499 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d618e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         499     4008217    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(1023, 254, 63) logical=(0, 0, 2)

According to the message in terminal I can't use fdisk on sda, the hd installed in the macbook. (a usb flash drive was attached at the time i ran  sudo fdisk -l).

What do you suggest i do now or instead? Although I have my OS X partition backed up I'd prefer to not ruin the drive and go through the process of restoring everything with time machine...

Does the guru have another suggestion?
I'd greatly appreciate it.

---

### Post by life_form on 2010-07-01
Alas, linuxopjemac.

[LEFT]I applied method 2 of the suggested ones. Worked like a charm. THANK YOU for pointing me in the right direction. I so much appreciate it! Awesome! back to Linux:popcorn:


Superduper.
[/LEFT]

---

