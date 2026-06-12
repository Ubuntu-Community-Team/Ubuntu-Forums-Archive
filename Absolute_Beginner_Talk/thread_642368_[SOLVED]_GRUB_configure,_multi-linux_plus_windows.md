---
title: "[SOLVED] GRUB configure, multi-linux plus windows"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by v.alari on 2007-12-16
I searched around google and the forums a bit and cant really find anything thats working for me.
Basically I have Windows XP, PCLinuxOS (which for some reason wont let me install without installing a bootloader so I have to install it first of the linuxes), Ubuntu, OPENsuse, Dreamlinux, and possibly something like Syllable but not worried about that for now.

Basically why its setup like this is I acquired a PC with 160GB HDD and a 40GB secondary and I wanted to learn linux. At the same time I am a gamer and until I can figure out linux enough to get my games working I need windows.

After installing XP I installed PCLinuxOS, nice graphical GRUB btw. Now I installed Ubuntu but I cant figure out how to configure GRUB to load all three. In fact I cant get it to load a memtest option either. I have pissed around with it for a while and it shows a option for Ubuntu now but gives a code 17: cannot mount selected partition error.

I have 
default 0
#timeout 10
#I dont want it to auto pick
color black/cyan yellow/cyan

##BEGIN AUTOMATIC KERNELS LIST

# memtest86=true

## ## End Default Options ##

title PCLinuxOS
kernel (hd0,1)/vmlinux BOOT_IMAGE=linux root=/dev/hda4 acpi=on
splash=silent vga=788
initrd (hd0,1)/initrd.img

(two other PCLinuxOS ones)

title Ubuntu
kernel (hd0,2)/vmlinux root=/dev/hda6 ro acpi=on
splash=silent
initrd (hd0,2)/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1

(another windows one I dont use)

##done

I dont know what (hd*,*) is for, please explain that as well.

---

### Post by overdrank on 2007-12-16
HI and maybe this link can help
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by v.alari on 2007-12-16
Iv been all over that page already, (hd*,*) was not explained, nor was multi linux booting, however through a link I found there, [http://www.linuxmigration.com/quickref/kernel/grub.html](http://www.linuxmigration.com/quickref/kernel/grub.html) ,I found more information on the subject.
The error 17: cannot mount partition was replaced by a error 23: cannot parse number.
Will get back to this thread later if I learn more and too see if further advice/research areas are offered.

---

### Post by logos34 on 2007-12-16
could you post

**sudo fdisk -l**

---

### Post by v.alari on 2007-12-17
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb77fb77

      Device Boot               Start                  End                       Blocks                 Id                   System
/dev/hda1   *                  15542              19457              31455270                   7                 HPFS/NTFS
/dev/hda2                               1                    38                  305203+              83                  Linux
/dev/hda3                         1997              15541            108800212+                5                  Extended
/dev/hda4                             39                1996              15727635                 83                  Linux
/dev/hda5                         1997                2034                  305203+              83                  Linux
/dev/hda6                         2035                3992               15727635+             83                  Linux
/dev/hda7                         3993                4030                  305203+              83                  Linux
/dev/hda8                         4031                5988                15727603+            83                  Linux
/dev/hda9                         5989                6026                  305203+              83                  Linux
/dev/hda10                       6027                7984                15727603+            83                  Linux
/dev/hda11                       7985              15541                60701571               83                 Linux

Partition table entries are not in disk order

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa153a153

        Device  Boot                 Start                 End                   Blocks            Id          System
/dev/hdb1                                 1                   131              1052226            82          Linux swap / Solaris
/dev/hdb2                           4736                  4865             1044225            82          Linux swap / Solaris
/dev/hdb3                             132                  4735            36981630             b          W95 FAT32

Partition table entries are not in disk order


I did finally get it to boot by using the script:
kernel (hd0,1)/vmlinuz ro root=/dev/hda6
initrd (hd0,1)/initrd.img

instead of the recommended ([http://www.linuxmigration.com/quickref/kernel/grub.html):](http://www.linuxmigration.com/quickref/kernel/grub.html):)
root (hd0,1)
kernel /boot/vmlinuz root=/dev/hda6

hda1 is windows
hda2 is /boot for PCLinuxOS
hda3 is / for PCLinuxOS
hda5 is /boot for Ubuntu and extended volume (obviously) 
hda6 is / for Ubuntu (also extended)

however since PCLinuxOS uses a different kernel version than Ubuntu 7.10 I am still having problems, Ubuntu issues errors and the networking doesnt work because its an older version. At least I think so because last time it worked "out of the box" and this time it does not


Changed name of vmlinuz etc and it loads new kernel now

---

### Post by shadow-of-sin on 2007-12-17
Explanation of hd(*,*): the first * is the hard drive number and the second * is the number of the partition. (note that numbering in GRUB starts at 0, so for example the first partition on the first hard drive would be: hd(0,0) etc.)

By the looks of your fdisk output, the Ubuntu portion of your menu.lst should look like this:
```
title Ubuntu
kernel (hd0,5)/vmlinux root=/dev/hda6 ro acpi=on
splash=silent
initrd (hd0,5)/initrd.img
```

---

### Post by v.alari on 2007-12-17
Well it works alright now, just curious what acpi=on and splash=silent are for. But its not really important though, just mainly posting to say thankyou. :)

---

### Post by logos34 on 2007-12-17
> **v.alari said:**
> Well it works alright now, just curious what acpi=on and splash=silent are for. But its not really important though, just mainly posting to say thankyou. :)

hmm...sounds like you're still using the pclinuxos /boot.  I would have thought this is the ubuntu entry you want:

> title Ubuntu
kernel (hd0,[COLOR="Red"]4[/COLOR])/vmlinu[COLOR="Red"]z-2.6.22-14-generic[/COLOR] root=/dev/hda6 ro acpi=on splash=silent
initrd (hd0,[COLOR="Red"]4[/COLOR])/initrd.img-2.6.22-14-generic

OR 

> title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,[COLOR="Red"]4[/COLOR])
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/hda6 ro splash quiet
initrd          /boot/initrd.img-2.6.22-14-generic


hda5 (hd0,4) is ubuntu /boot, hda6 is root.  You need the '2.6.22-14-generic' part because that's how their named in boot 

And then you'd need to reinstall grub to mbr pointing to ubuntu /boot (hd0,4).

But if it works now, hey, leave it.

---

