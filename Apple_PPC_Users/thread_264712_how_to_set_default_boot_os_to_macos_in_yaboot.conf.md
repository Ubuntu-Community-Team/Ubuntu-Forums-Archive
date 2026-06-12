---
title: "how to set default boot os to macos in yaboot.conf?"
date: 2006-09-25
forum: Apple PPC Users
---

### Post by baosheng on 2006-09-25
Hi guys,

I have read the man page of yaboot.conf.

in the yaboot.conf, I set 
[INDENT]defaultos=macos[/INDENT]
and I also set
[INDENT]maxos=/dev/hda9[/INDENT]

But when the computer boots, it doesn't go to Mac OS 9.2, but to linux.

Following is my fdisk -l result
--------------------------------------------------------
forrest@forrest-mac:~$ sudo fdisk -l
Password:
/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map &#443;&#65533;&#65533;                     63 @ 1        ( 31.5k)  Partition map
/dev/hda2          Apple_Driver43 Macintosh                54 @ 64       ( 27.0k)  Driver 4.3
/dev/hda3          Apple_Driver43 Macintosh                74 @ 118      ( 37.0k)  Driver 4.3
/dev/hda4        Apple_Driver_ATA Macintosh                54 @ 192      ( 27.0k)  Unknown
/dev/hda5        Apple_Driver_ATA Macintosh                74 @ 246      ( 37.0k)  Unknown
/dev/hda6          Apple_FWDriver Macintosh               200 @ 320      (100.0k)  Unknown
/dev/hda7      Apple_Driver_IOKit Macintosh               512 @ 520      (256.0k)  Unknown
/dev/hda8           Apple_Patches &#65533;&#1970;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;            512 @ 1032     (256.0k)  Unknown
/dev/hda9               Apple_HFS &#948;&#65533;&#65533;&#65533;&#65533;             39100772 @ 1544     ( 18.6G)  HFS
/dev/hda10             Apple_Free &#65533;&#65533;&#65533;&#65533;                     20 @ 39102316 ( 10.0k)  Free space

Block size=512, Number of Blocks=39102335
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 23, type=0x1
2: @ 118 for 36, type=0xffff
3: @ 192 for 21, type=0x701
4: @ 246 for 34, type=0xf8ff

/dev/hdb
        #                    type name                length   base    ( size )  system
/dev/hdb1     Apple_partition_map Apple                   63 @ 1       ( 31.5k)  Partition map
/dev/hdb2         Apple_Bootstrap untitled              1954 @ 64      (977.0k)  NewWorld bootblock
/dev/hdb3         Apple_UNIX_SVR2 untitled           7994141 @ 2018    (  3.8G)  Linux native
/dev/hdb4         Apple_UNIX_SVR2 swap                422657 @ 7996159 (206.4M)  Linux swap

Block size=512, Number of Blocks=8418816
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 23, type=0x1
2: @ 118 for 36, type=0xffff
3: @ 192 for 21, type=0x701
4: @ 246 for 34, type=0xf8ff
----------------------------------------------------

And this is my /etc/yaboot.conf
[B]
boot=/dev/hdb2
device=/pci@f2000000/pci-bridge@d/mac-io@7/ata-4@1f000/disk@1:
partition=3
delay=10
root=/dev/hdb3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot

fgcolor=black
bgcolor=green

enablenetboot
enablecdboot

default=Linux
defaultos=macos

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="quiet splash"

macos=/dev/hda9[/B]

---

### Post by dearvoid on 2006-09-28
After you modified "/etc/yaboot.conf" you must run "ybin" to make it take effect.

---

