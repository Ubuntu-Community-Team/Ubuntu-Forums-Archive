---
title: "[SOLVED] Windows not working, Ubuntu is"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by xzin on 2007-12-12
Hi, I'm having problem with my ubuntu/windows xp install. Yesterday I reinstalled my windows, and after that I installed ubuntu, and set it to use "biggest free space available" or sometinh like that, can't remember exactly.

So, my ubuntu install is working perfectly, but when I try to select the windows XP install from the list, it just gives me "starting up..." and freezes. I know that all the windows files are there, because if I "fix" windows install with windows CD using the "fixmbr" command. That removes grub completely, and automatically starts windows.

Please help me to get them both work :)

---

### Post by meborc on 2007-12-12
> **xzin said:**
> Hi, I'm having problem with my ubuntu/windows xp install. Yesterday I reinstalled my windows, and after that I installed ubuntu, and set it to use "biggest free space available" or sometinh like that, can't remember exactly.

So, my ubuntu install is working perfectly, but when I try to select the windows XP install from the list, it just gives me "starting up..." and freezes. I know that all the windows files are there, because if I "fix" windows install with windows CD using the "fixmbr" command. That removes grub completely, and automatically starts windows.

Please help me to get them both work :)

so if you use windows disk to reinstall MBR... and then recover grub, windows still doesn't start? 

if you haven't tried it yet, i think you should... this will help you after you have used the windows disk - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by xzin on 2007-12-12
Yes, I tried that. I reinstalled grub with the live CD, and then ubuntu was working again, but windows was not.

---

### Post by jspangler on 2007-12-12
Could you post the output from the terminal of the command:

```
sudo fdisk -l
```


Then, could you post the output of:

```
cat /boot/grub/menu.lst
```

---

### Post by dstew on 2007-12-12
This problem can have several causes. Sometimes, it is because the Windows boot partition is not properly named in grub's menu.lst file. Sometimes, Windows itself cannot boot because the menu.lst entry is not in the correct form. Sometimes, the Windows install is not in a primary partition, which causes failure.

To get an idea of what is going on, please post the output of the commands
```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by xzin on 2007-12-12
```
sudo fdisk -l
```

gives me:

Levy /dev/sda: 320.0 Gt, 320072933376 tavua
255 päätä, 63 sektoria/ura, 38913 sylinteriä
Yksiköt = 16065 * 512 = 8225280 -tavuiset sylinterit

    Laite Käynn     Alku          Loppu    Lohkot   Id  Järjestelmä
/dev/sda1   *           1       20086   161340763+   7  HPFS/NTFS
/dev/sda2           20087       38156   145147275   83  Linux
/dev/sda3           38157       38913     6080602+   5  Laajennettu
/dev/sda5           38157       38913     6080571   82  Linux / Solaris heittovaihtotiedosto

```
cat /boot/grub/menu.lst
```[/QUOTE]

gives me 

)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=154a46e9-0711-4fc4-bc1a-dc8aeb323b07 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash noapic locale=fi_FI

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=154a46e9-0711-4fc4-bc1a-dc8aeb323b07 ro quiet splash noapic locale=fi_FI
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=154a46e9-0711-4fc4-bc1a-dc8aeb323b07 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

I'm sorry that some parts are in Finnish, if you need something translated, just say :)

---

### Post by dstew on 2007-12-12
It looks correct to me. Windows is in a primary partition, boot flag is set, and the menu.lst entry seems OK. There is another thought. Sometimes, the BIOS drives do not enumerate the same way as the Linux drives. That is, Linux says the Windows partition is /dev/sda1, which *should* be the same as hd0,0. However, if the BIOS thinks that drive is hd1, there will be a problem. I don't know how to check the BIOS enumeration, but there is a file in Linux to check:```
cat /boot/grub/device.map
```Please post the result of this command.

---

### Post by xzin on 2007-12-13
```
cat /boot/grub/device.map
``` 

(hd0)   /dev/sda

---

### Post by doudeman on 2007-12-13
If thats not the most ironic title...

---

### Post by xzin on 2007-12-13
Anyone able to help?

---

### Post by nikolas68 on 2007-12-13
Insert setup DVD and select "system Start Repair". If it doesn't work boot the repair console in Windows and enter the command 

```
bootrec /fixmbr
```

hope it works!

---

### Post by xzin on 2007-12-13
> **nikolas68 said:**
> Insert setup DVD and select "system Start Repair". If it doesn't work boot the repair console in Windows and enter the command 

```
bootrec /fixmbr
```

hope it works!

Do you mean the Windows install CD?

---

### Post by dstew on 2007-12-13
Another thought. Maybe when you installed grub, it put part of itself into the first sector of the first partition of the disk, that is, it went into hd0,0. It might then boot Ubuntu, but if you use chainloader +1, the Windows booter will not find its part, but only a part of grub. I vaguely remember a problem like this. When you install grub, you have to tell it to install in hd0, and not in hd0,0. If you use hd0, it will install in the MBR only. If you use hd0,0, it will go into the first sector of the first partition. Since that sector is tagged as bootable, the BIOS will bring up grub, but when grub tries chainload +1 with root hd0,0 it messes up. Just a thought.

---

### Post by xzin on 2007-12-13
> **dstew said:**
> Another thought. Maybe when you installed grub, it put part of itself into the first sector of the first partition of the disk, that is, it went into hd0,0. It might then boot Ubuntu, but if you use chainloader +1, the Windows booter will not find its part, but only a part of grub. I vaguely remember a problem like this. When you install grub, you have to tell it to install in hd0, and not in hd0,0. If you use hd0, it will install in the MBR only. If you use hd0,0, it will go into the first sector of the first partition. Since that sector is tagged as bootable, the BIOS will bring up grub, but when grub tries chainload +1 with root hd0,0 it messes up. Just a thought.

I'll try this, and report how it works.

---

### Post by xzin on 2007-12-13
No success. I installed Grub with your instructions and checked also from this thread
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Following orders, i entered
 ```
find /boot/grub/stage1
```

This returned (hd0,1) for me, so Next i wrote

```
root (hd0,1)
```

This didnt work with (hd0), I tried.

Then I wrote 
```
setup (hd0)
```

Which installed grub succesfully. Now, my Ubuntu is working again, but windows isnt.
More advices, if you have any. If I have to, I can reinstall both, I just want them to work.

---

### Post by dstew on 2007-12-13
That is the correct way to install grub. It now has its stage 1 in the hd0 MBR, and it will get its stage 2 and menu from hd0,1

It seems that the Windows boot sector (the first sector in hd0,0) is not working. You can replace this with a good boot sector by using the **fixboot** command from the Windows recovery console. Note the command is fixboot and not fixmbr. The fixmbr command will write over grub stage 1. You need to supply fixboot with the Windows drive designation. If hd0,0 is D: , then the command is **fixboot d:**

---

### Post by xzin on 2007-12-13
Didnt work. I wrote
**fixboot c:**
And it was succesful. I restarted my computer and got to the grub selection screen just fine.
Selected Windows Xp, and it freezed to the same starting up...

---

### Post by dstew on 2007-12-13
Other thoughts. According to the grub manual, sometimes instead of root you need to use **rootnoverify** in the boot commands. See [http://www.gnu.org/software/grub/manual/grub.html#Booting](http://www.gnu.org/software/grub/manual/grub.html#Booting)
To be honest, I have never heard of anybody using this and having success, but it might work. You can try different booting commands from the grub command line, the same thing you used when you installed it. Like this:```
grub> rootnoverify (hd0,0)
grub> makeactive
grub> chainloader +1
grub> boot
```
Clearly, I am running out of ideas.

---

### Post by xzin on 2007-12-13
```
grub> rootnoverify (hd0,0)
grub> makeactive
grub> chainloader +1
grub> boot
```

Thanks, I'll try this. If it doesn't work and no one comes up with more ideas, I guess I will just reinstall both :)

---

### Post by xzin on 2007-12-14
Just an idea, could I use Lilo instead of Grub? Or is it even meant for same thing, I just saw it somewhere.

---

### Post by meindian523 on 2007-12-14
Lilo IS used for the same purpose as Grub,only it's really old,tho' some people prefer to use it over grub.....

---

### Post by xzin on 2007-12-14
After thinking what I really need windows for, I have decided to remove completely my windows install and use whole hard drive for ubuntu. If I really need windows for something, I can use virtualbox. And what I checked, most of the games work fine with Wine.

So, now my question is, how can I resize my partitions, so I could completely remove my existing windows partition and resize ubuntu partition to make it bigger? Or would it be easier to just reinstall ubuntu? I already installed QTparted, and looked at it, but didnt find option to resize ubuntu partition, only windows partition.

---

### Post by Teknyk on 2007-12-14
I do believe this is the first time I have seen someone get sick of windows and "go back to Linux" :lolflag:

Oh yeah, If you're just going to use the whole hard drive let the live cd load and click install. let it walk you through.

---

### Post by xzin on 2007-12-14
Thanks for reply.
Goodbye windows ):P
edit: Oh, I could mark this as "solved" :D

---

### Post by xzin on 2007-12-14
Thanks for reply.
Goodbye windows ):P
Oh, this could be marked as "solved" :lolflag:

---

### Post by greg_g on 2007-12-14
> **xzin said:**
> 
Oh, this could be marked as "solved" :lolflag:

You can do that under the "Thread Tools" menu at the top of this page.

---

### Post by lvleph on 2007-12-14
> **Teknyk said:**
> I do believe this is the first time I have seen someone get sick of windows and "go back to Linux" :lolflag:

Oh yeah, If you're just going to use the whole hard drive let the live cd load and click install. let it walk you through.

That is what I have done too. I kept having a BSOD couldn't load p3.sys. I even got it in my virtualized windows. I figure it was probably a virus, or something.

---

### Post by quandary on 2007-12-14
> **meindian523 said:**
> Lilo IS used for the same purpose as Grub,only it's really old,tho' some people prefer to use it over grub.....

Yes - true, and I understand them. It's true that LILO is old, but this preference is, because LILO actually works, whereas Grub... [CENSORED] ... well just look at all the Grub threads in this forum...

But whatever, you just have to adjust the drive number:
root		(hd0,0)
becomes
root		(hd1,0)

and vice/versa

in this case only for the windows section...

---

