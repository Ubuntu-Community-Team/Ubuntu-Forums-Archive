---
title: "Help!! I cant boot m$ win after installing linux"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Ghost Face on 2008-04-08
Help!! I cant boot m$ win after installing linux, problem=no such partition!

title Microsoft Windows XP Professional
**[COLOR="Red"]root (hd0,0)[/COLOR]**
savedefault
makeactive
chainloader +1


```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000986d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       16708   134206978+   f  W95 Ext'd (LBA)
/dev/sda5            1020       16708   126021861    7  HPFS/NTFS
/dev/sda6               1        1019     8185023   83  Linux

```

---

### Post by R6V2 on 2008-04-08
When installing did you choose to overwrite your disk with Linux?

---

### Post by Ghost Face on 2008-04-08
no, i have just installed it on fresh created fat32 partition, im using linux 1 year+ and i never had that probelm.

---

### Post by very_japi on 2008-04-08
Could you be a little more explicit?

---

### Post by Ghost Face on 2008-04-08
I have edited menu.lst grub file and added Win XP Pro, and i tried to boot win os and i get no such partiton problem. 

title Microsoft Windows XP Professional
**[COLOR="Red"]root (hd0,0)[/COLOR]** - this is the problem, and i dont know what numers should i write instead of 0,0 :S
savedefault
makeactive
chainloader +1

---

### Post by ibutho on 2008-04-08
Try the following
```

title Microsoft Windows XP Professional
    root (hd0,4)
    savedefault
    makeactive
    chainloader +1

```

---

### Post by Ghost Face on 2008-04-08
OK, brb. :)

---

### Post by Ghost Face on 2008-04-08
> **ibutho said:**
> Try the following
```

title Microsoft Windows XP Professional
    root (hd0,4)
    savedefault
    makeactive
    chainloader +1

```

Invalid Device Requested

---

### Post by Ikith on 2008-04-08
try 0,1

---

### Post by red_Marvin on 2008-04-08
If it doesn't work, you might be interested in [this]("http://www.gnu.org/software/grub/manual/html_node/Device-syntax.html#Device-syntax") page to find out what numbers to put.

---

### Post by fearnloathing55 on 2008-04-08
I'm pretty sure I have the exact same problem, I also get the "Invalid Device Requested" error. 

This is my fdisk -l 

> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x001e001e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+  83  Linux
/dev/hda2            1913        8572    53496450    f  W95 Ext'd (LBA)
/dev/hda3            8573        9729     9293602+   b  W95 FAT32
/dev/hda5            1913        8514    53030533+   7  HPFS/NTFS
/dev/hda6            8515        8572      465853+  82  Linux swap / Solaris



My menu.lst entry-

> 
title		Windows XP Professional
rootnoverify    (hd0,4)
savedefault
makeactive
chainloader	+1

And df returns - 

> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             15116836  10538392   3810540  74% /
varrun                  517304       104    517200   1% /var/run
varlock                 517304         0    517304   0% /var/lock
udev                    517304        92    517212   1% /dev
devshm                  517304         0    517304   0% /dev/shm
lrm                     517304     16488    500816   4% /lib/modules/2.6.22-14-generic/volatile
/dev/hda3              9284512         8   9284504   1% /windows
/dev/sda1            244196000 117912920 126283080  49% /media/FreeAgent Drive
wilsona@res061-244:~$ 


(Note- changing the boot flag to a different drive doesn't get rid of the error, I tried that already. Also the partition with windows on it is hda5, not hda3)

---

### Post by Ikith on 2008-04-08
> **red_Marvin said:**
> If it doesn't work, you might be interested in [this]("http://www.gnu.org/software/grub/manual/html_node/Device-syntax.html#Device-syntax") page to find out what numbers to put.

According to this (And knowledge since I took linux cert class rofl) it should be 0,1 since its still on the hard drive and its on what seems to be the 2nd partition :-P! I hope it's 0,1 anyway.

@Fearn: Yours should be 4,0


I gotta know why people are still using FAT32... It makes this a bit more confusing roflz!

---

### Post by ByteJuggler on 2008-04-08
Never mind, I gave incorrect advice.  (tired..)

---

### Post by Ghost Face on 2008-04-08
its not 0,1 :S

---

### Post by Ghost Face on 2008-04-08
I have installed PClinuxOS and no windows option again! AAAAAAAAAA

grub menu.lst
```
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,5)/usr/share/gfxboot/themes/pclos-gnome/boot/message
default 0

title linux
kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sda6  acpi=on splash=silent vga=788
initrd (hd0,5)/boot/initrd.img

title linux-nonfb
kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/sda6  acpi=on
initrd (hd0,5)/boot/initrd.img

title failsafe
kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/sda6  failsafe acpi=on
initrd (hd0,5)/boot/initrd.img
```

---

### Post by dummyhead3 on 2008-04-08
try

title Windows XP Professional
rootnoverify (hd0,2)
savedefault
makeactive
chainloader +1

---

### Post by fearnloathing55 on 2008-04-08
Mine still doesn't work, but I did turn up something interesting. When I open gparted it tells me that it can't read the contents of hda5, also hda3 (not hda5) is mounted on /windows. Shouldn't hda5 be mounted there if it's the partition I'm trying to boot from? If so, how do I change that? If that's not it then I have no idea what's wrong :-?

---

### Post by Ghost Face on 2008-04-09
> **Ghost Face said:**
> I have installed PClinuxOS and no windows option again! AAAAAAAAAA

grub menu.lst
```
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,5)/usr/share/gfxboot/themes/pclos-gnome/boot/message
default 0

title linux
kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sda6  acpi=on splash=silent vga=788
initrd (hd0,5)/boot/initrd.img

title linux-nonfb
kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/sda6  acpi=on
initrd (hd0,5)/boot/initrd.img

title failsafe
kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/sda6  failsafe acpi=on
initrd (hd0,5)/boot/initrd.img
```

Anyone??

---

### Post by gator64 on 2008-04-09
Quick question Ghost Face - can you access the files on your Windows partition from Ubuntu ?

---

### Post by Ghost Face on 2008-04-09
> **gator64 said:**
> Quick question Ghost Face - can you access the files on your Windows partition from Ubuntu ?

yes i can

---

