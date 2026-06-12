---
title: "Urgent GRUB Problem"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by dfault312 on 2007-12-26
I just decided to setup my XP machine to dual boot Ubuntu with a second hard drive. everything went great, until I tried to boot for the first time. I need to fix this problem tonight, and at least get XP to boot again, because I am going to be out of town for a week, and my dad needs to use XP.

Grub gets to stage 1.5 and then gives Error 21, which I'm assuming means "can't find disk". I have 2 internal disks and two external disks;

Internal:
/dev/sda 80GB NTFS hd0,0
/dev/sdb 6GB ext2 hd1,0

External:
/dev/sdd 250GB FAT32 hd2,0
/dev/sde 4GB FAT32 hd3,0

here's some outputs that might help explain things:

$sudo gedit /boot/grub/menu.lst
> 
## default num
default		0

## timeout sec
timeout		10

## hiddenmenu
#hiddenmenu

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
# kopt=root=UUID=9857da4b-5023-4d36-968f-18bb8519b04a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet splash

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9857da4b-5023-4d36-968f-18bb8519b04a ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9857da4b-5023-4d36-968f-18bb8519b04a ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

$sudo fdisk -l
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9725    78116031    7  HPFS/NTFS

Disk /dev/sdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xba94ba94

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         752     6040408+  83  Linux
/dev/sdb2             753         784      257040   82  Linux swap / Solaris

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30401   244196001    c  W95 FAT32 (LBA)

Disk /dev/sde: 4126 MB, 4126146560 bytes
16 heads, 32 sectors/track, 15740 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x2c1d7047

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       15740     4029424    c  W95 FAT32 (LBA)


---

### Post by jas0 on 2007-12-26
Unfortunately, on first look everything looks good to me. But if you need to urgently get Windows working and you don't have time to mess around with your boot.lst file, try following this guide:

[http://users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console]("http://users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console")

I'm linking to the easiest way to do this, but you can follow any of the methods on the page. Also, if you manage to solve your problem without removing Ubuntu, set the default boot num to 3 (I think). You don't want your dad to be confused when he starts the computer and sees the Ubuntu login screen!

Good luck!

---

### Post by meierfra on 2007-12-26
If you are lucky you might be able to solve your problem just by changing the boot order in the bios. The order needs to be

sda
sdb
sdd
sde

(Edit: Ignore the remainder of this post. The dualtwo howto can not be applied directly) If this did not solve the problem click on "dualtwo" in my signature.  That howto should solve your problem. The howto assumes that ubuntu is on an external drive, but that is irrelevant. Whenever its  says "external drive" just read it as  sdb,  your ubuntu drive.

If you need more help, let me know..

---

### Post by meierfra on 2007-12-26
To quickly restore Windows, click on FixMBR in my signature. The first two method's also appear in jas0 link. The third one can be done just using the Ubuntu LiveCD..

---

### Post by meierfra on 2007-12-26
Forget about the "dualtwo" howto. It does not apply in your case. Let me know if changing the boot order did not solve your problem. I will give you a modified version of the dualtwo howto, tailored to your situation and which can be done from the ubuntu "LiveCD"

---

### Post by perfecxion on 2007-12-26
I think it maybe as simple as running update-grub, that is if you can boot into Ubuntu. If not the easiest way to fix this is use a gparted CD wipe Ubuntu and install it again then it should work. Your third option use gparted CD wipe Ubuntu and use your windows XP cd to fix the boot file for it. The way you do that is just put the installation CD boot the computer up and select the option repair. Hope that helps.

And you get the Gparted CD from: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and select the liveCD to get the gui one.

---

### Post by dfault312 on 2007-12-26
well, i ran the XP recovery console and did fixmbr. im booting windows only now. thanks for all the quick responses! i'll have to fix my linux boot later, after vacation.

---

### Post by meierfra on 2007-12-26
```
update-grub, 
```

That would not change anything.


>  wipe Ubuntu 

That would not help booting Windows. Fixing the MBR (as already suggested by two different people in this thread) will work  regardless whether Ubuntu is installed or not.

---

### Post by meierfra on 2007-12-27
Then this is for when  you come back from your vacation:

No need to wipe ubuntu.
Boot from Ubuntu LiveCD. Open a terminal (Applications->Accessories->Terminal)


Step 1 Edit menu.lst

```
mkdir ubuntu
sudo mount -t ext3 /dev/sdb1 ubuntu
cd ubuntu/boot/grub
sudo cp menu.lst menu.lst.backup
gksudo gedit menu.lst
```


Change "default 0" to "default 4"  (If  you want the computer to boot into Windows by default)

You might also want to change "#hiddenmenu" to "hiddenmenu" and "timeout 10" to "timeout 3"  to hide the grub menu and reduce the length of the pause  before the default boot.

Change "groot (hd1,0)" to "groot (hd0,0)"

Change all "root (hd1,0)"   in the titles section to "root (hd0,0)" . There are three of them.

Change

title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

to

title Microsoft Windows XP Home Edition
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1 

Save the file

Step 2 Reinstall Grub

```
sudo grub
```
and at the grub prompt:

```
root (hd1,0)
setup (hd1)
quit
```

Step 3 Reboot, but change the boot order  such that sdb (the ubuntu drive) is first in the boot order and  sda (the windows drive) is second.

That's it


Note that this installs Grub to the MBR of the Ubuntu drive. So if something happens to Ubuntu, you still will be able to boot into Windows, just by booting from the Windows drive.

Also  you won't have to reinstall Grub each time you reinstall Windows.

---

