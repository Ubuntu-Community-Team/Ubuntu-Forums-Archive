---
title: "Triple Booting?"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by minimidgy on 2005-06-20
I am currently dual-booting with Ubuntu Hoary 5.04 and Windows XP.  I want to try out Linspire just for fun, but I don't want to get rid of Ubuntu.  Is it possible to triple boot?

---

### Post by bored2k on 2005-06-20
[QUOTE=minimidgy]I am currently dual-booting with Ubuntu Hoary 5.04 and Windows XP.  I want to try out Linspire just for fun, but I don't want to get rid of Ubuntu.  Is it possible to triple boot?[/QUOTE]
 Yes. If you install Linspire after Ubuntu and Windows, I'm really not sure if Linspire has a efficient boot loader -if any-. But if you use ubuntuguide.org's recovering Grub trick, you should be able to.

---

### Post by minimidgy on 2005-06-20
[QUOTE=bored2k]Yes. If you install Linspire after Ubuntu and Windows, I'm really not sure if Linspire has a efficient boot loader -if any-. But if you use ubuntuguide.org's recovering Grub trick, you should be able to.[/QUOTE]
would I have to take away space from one of my current partitions and allow Linspire to use it? I had trouble doing something similar to that once before.

---

### Post by Xian on 2005-06-20
It's very straightfoward. When you install Linspire just make sure you tell the installer to NOT install the bootloader to the MBR. Instead, direct it to the Linspire root (or /boot partition if it exists) partition. This way it will have no impact on your current grub setup.

Then you simply go into Ubuntu's /boot/grub/menu.lst and add the appropriate entries that would correspond to Linspire's kernel and related info. It is quite intuitive and if you need help just post back.

---

### Post by Xian on 2005-06-20
[QUOTE=minimidgy]would I have to take away space from one of my current partitions and allow Linspire to use it? I had trouble doing something similar to that once before.[/QUOTE]
You'll have to create some free space if you don't currently have any. Use the command below to see if it presently exists on your HD. If not, it is much easier to resize Windows than Linux and get your space in that fashion.

```
$ sudo cfdisk
```
My output:

```
 cfdisk 2.12p

                              Disk Drive: /dev/hda
                       Size: 160041885696 bytes, 160.0 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 19457

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    hda1                    Primary   NTFS                             26853.09*                              
    hda2        Boot     Primary   Linux ext3                     12880.79
    hda3                    Primary   Linux ext3                     10741.99*                         
    hda5        NC        Logical   Linux swap                    1077.48*    
    hda6                    Logical   Linux ext3                      5371.11
    hda7                    Logical   Linux ReiserFS               21467.99
    hda8                    Logical   Linux ReiserFS               29997.60
    hda9                    Logical   W95 FAT32                    10503.69
                            Logical   Free Space                       41142.86

     [Bootable]  [ Delete ]  [  Help  ]  [Maximize]  [ Print  ]
     [  Quit  ]  [  Type  ]  [ Units  ]  [ Write  ]

```

---

### Post by minimidgy on 2005-06-20
okay I currently have 20 GB set to windows, and I want to make it only 10 GB. How do I do this?

---

### Post by Xian on 2005-06-20
I personally use the Ubuntu Install CD to partition and resize my HD with, and when finished just abort the process and reboot. It's great because I don't have to worry about being sure that certain partitions are not mounted, and it uses parted which is a rock solid partition application. 

However, you can also use qtparted or gparted which are available in Synaptic if you would prefer to do your resizing while logged into Ubuntu, and it also does have a nice looking GUI. The process is the same as with the InstallCD save that just remember to umount all applicable partitions.

Then of course there are Win-based programs like Partition Magic, Acronis, and so forth.

---

