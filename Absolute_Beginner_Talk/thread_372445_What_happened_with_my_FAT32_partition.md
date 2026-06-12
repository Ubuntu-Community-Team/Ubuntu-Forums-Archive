---
title: "What happened with my FAT32 partition?"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by JesCed on 2007-02-28
Hello, all.

I've been using Kubuntu Edgy for some time now. Besides the Linux partitions, I also have two additional partitions on my drive. I have an NTFS partition (I dual-boot with WinXP) and a FAT32 partition, which I use as space that can be read/write under both OSs. This normally didn't pose any problem, except that I was suddenly unable to see the contents of the FAT32 partition under kubuntu. The /media/Win32 folder does exist, but is completely blank when I open it. In fact, when I use the "storage devices" shortcut on the taskbar I see both my WinXP and Win32 devices, but the former has a "device" icon, while the latter has a common folder icon. Also in that list are two folder icons representing USB drives that are currently not mounted (nor, in fact, even plugged in)

When I boot into WinXP I can see the contents of the FAT32 partition (my "F" drive) perfectly, so I know my data is still there.

Can anyone explain what happened here, and tell me how to get this issue sorted out?

---

### Post by yabbadabbadont on 2007-02-28
Please post the contents of your /etc/fstab file and the output of "sudo fdisk -l" when run in a terminal window.

---

### Post by JesCed on 2007-02-28
OK. Here's my /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6 -- converted during upgrade to edgy
UUID=081852fd-63ab-45ba-a8bc-609d0130f499 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=34fa7c2e-2de3-4616-a14c-4de6963194b7 /home ext3 defaults 0 2
# /dev/hda4 -- converted during upgrade to edgy
UUID=D392-FEA1 /media/Win32 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=F0C891E6C891AB7C /media/WinXP ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=470c5c84-8213-40e8-b5bd-83d9019eb266 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


And here's the output:

Disco /dev/hda: 40.0 GB, 40060403712 bytes
255 cabezas, 63 sectores/pista, 4870 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1   *           1        3061    24587451    7  HPFS/NTFS
/dev/hda2            4095        4580     3903795   83  Linux
/dev/hda3            3062        4094     8297572+   5  Extendida
/dev/hda4            4581        4870     2329425    b  W95 FAT32
/dev/hda5            4022        4094      586341   82  Linux swap / Solaris
/dev/hda6            3062        4021     7711137   83  Linux

Las entradas de la tabla de particiones no están en el orden del disco

---

### Post by taurus on 2007-02-28
Edit /etc/fstab

```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```
and replace this line

```
UUID=D392-FEA1 /media/Win32 vfat defaults,utf8,umask=007,gid=46 0 1
```
with this one.

```
/dev/hda4  /media/Win32 vfat defaults,utf8,umask=007,gid=46 0 1
```
Save it and reboot.

---

### Post by JesCed on 2007-03-01
Thanks very much. That solved the issue. However, I still have some lingering questions. and would very much like to know the answers.

1.- What actually happened? From the solution I'm guessing that the renaming of partitions during the upgrade to edgy somehow messed things up, but the problem didn't appear just after upgrading. I upgraded in november, and was able to use my FAT32 partition without problems until last week.

2.- Even though renaming didn't affect my other partitions, should I edit /etc/fstab so all new names are replaced by their /dev/hd* equivalents, or should I just leave well enough alone?

3.- Why are the two USB drives I mentioned still displayed in the 'storage devices' window even when not plugged in? This isn't really a mejor issue, as the drives still mount/unmount and work perfectly, but it still kind of irks me.

Thanks, all, in advance

---

