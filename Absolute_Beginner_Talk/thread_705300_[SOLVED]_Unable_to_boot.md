---
title: "[SOLVED] Unable to boot"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by ophilar on 2008-02-23
Hi,

I'm quite new to Linux. I had Kubuntu KDE4 and Windows XP on an Lenovo X41 Tablet.
Yesterday I tried to create a new partition to separate my data from my system files (on WinXP). I created a Logical partition on the linux-swap partition, and moved the Kubuntu partition into it by copying and deleting the original.
The system wouldn't boot afterwards. I got grub error 17. I played around using sysrescd (running on usb flash drive), and gotten to error 22.
But then I get "A disk read error, press ctrl+alt+delete to restart" and "1234f:" command all the time. I guess I ruined the mbr.
I tried testdisk a few times, but I can't get it to set the partitions right - it doesn't see the predesktop partition which contains the WinXP install, and doesn't let me set the linux partition to logical.

For the record I don't have a cd drive available for this computer.

What can I do about it? Is there a way for me to fix the mbr at all? Is the mbr the problem?

I have my valuable data backed up, but I still don't want to send it to tech support, because I'll have to start w/ linux all over again...
I'm desparate!

Tx, Ron

---

### Post by ichbinesderelch on 2008-02-23
i guess the problem is that when you moved your hdds grub(the boot loader) got messed up, you should kinda try booting with a live cd or something and do a grub reinstallation!
this could help: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by ophilar on 2008-02-23
Can you tell me how do I reinstall grub, using a usb? I think there's grub on the sysrescd I use...

---

### Post by sandysandy on 2008-02-23
restoring MBR is not a problem. An utility called Super Grub Disk allows u to do that.

Have a look at this link on grub errors
[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html)

it defines error 22 as follows:-

22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 
 have a link at this site also

[http://users.bigpond.net.au/hermanzone/p15.htm#orientation](http://users.bigpond.net.au/hermanzone/p15.htm#orientation)

u may have to edit menu.lst file

regards

---

### Post by ophilar on 2008-02-23
Thanks.
I already changed the menu.lst. Right now I don't even get to grub bootloader - I get errors before that. I'll check the super grub.

---

### Post by ophilar on 2008-02-23
I reinstalled grub and now can work with my Linux again. But WinXP is not booting, still leaving the "Disk read error...". And I can't see the predesktop partition.

---

### Post by divindavid on 2008-02-23
you could alaways get a usb CD/DVD

---

### Post by dstew on 2008-02-23
If you get the grub menu, but the Windows menu item doesn't work, you probably have to edit the file /boot/grub/menu.lst. To know exactly how to edit that file, enter the command```
sudo fdisk -l
```and post the result to the forum. Also, post the output of```
cat /boot/grub/menu.lst
```Then we will know exactly what to do.

---

### Post by ophilar on 2008-02-23
sudo fdisk -l:
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008970e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1958    15727603+   7  HPFS/NTFS
/dev/sda2            1959        2089     1052257+   f  W95 Ext'd (LBA)
/dev/sda3            2090        3003     7341705   83  Linux
/dev/sda4            3004        4318    10562737+   7  HPFS/NTFS
/dev/sda5            1959        2089     1052194+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 1030 MB, 1030225920 bytes
4 heads, 3 sectors/track, 167680 cylinders
Units = cylinders of 12 * 512 = 6144 bytes
Disk identifier: 0x0009e8b5

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1              21      167680     1005958+   b  W95 FAT32

*******************
cat /boot/grub/menu.lst:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         3

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
# kopt=root=UUID=1942bf96-e63a-4a56-8273-600bf966f718 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=1942bf96-e63a-4a56-8273-600bf966f718 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=1942bf96-e63a-4a56-8273-600bf966f718 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
rootnoverify            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title           Windows NT/2000/XP
rootnoverify            (hd0,3)
savedefault
makeactive
chainloader     +1

---

### Post by Papa.Gario on 2008-02-23
I'm having a problem similar to yours -- Linux starts fine, but trying to boot Windows gives me the error.  Good luck finding a fix, If I an figure it out I'll try to help.

So far reinstalling grub didn't help.
Doing a complete reinstall of Ubuntu didn't help.
Repairing Windows didn't help, just made it worse.

SuperGrub can boot from USB, [Here's the download]("http://supergrub.forjamari.linex.org/?section=download")

I ran out of disks and was having to do everything from usb too :)

---

### Post by dstew on 2008-02-23
It looks to me from your fdisk output, and your /boot/grub/menu.lst that grub is set up properly. If Windows won't boot, you may have a problem with your Windows boot sector on that /dev/sda1 partition. You can fix that by using the **fixboot** command from the Windows CD Recovery Console.

---

### Post by Papa.Gario on 2008-02-23
How do you run fixboot?  

I don't have a windows recovery disc, I just have the recovery partition.

---

### Post by dstew on 2008-02-23
You probably have to boot from your recovery partition. How to do that depends on your hardware. You probably have the option to press one of the function keys at boot-time to get into the recovery. You will have to consult your computer's manual to see exactly what to do.
Unfortunately, some recovery system will overwrite your grub in the MBR. If it takes that to get your Windows functional again, that is OK, because we can just re-install grub later.

The supergrub disk may be able to do the equivalent of fixboot. It is restoring the NTLDR (NT loader) to the Windows partition (*not* the MBR). See [this]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") and [this]("http://supergrub.forjamari.linex.org/").

---

### Post by ophilar on 2008-02-23
My recovery partition is not usable right now - the computer doesn't see it, or rather it does - as free non-partitioned space. I think that what hacked it all was that I tried putting linux in a logical partition. Right now I have 4 partitions already. I'll delete the empty one, and with any luck will gain the recovery partition. But then, supergrub can be used from USB flash, so it might be safer. Will let you know the outcome.

---

### Post by sandysandy on 2008-02-23
u may like to [COLOR="Blue"]boot [/COLOR]ur computer [COLOR="Blue"]with the bootable Super Grub Disk [/COLOR]and using this utility try [COLOR="Blue"]booting ur windows partition[/COLOR]. this utility is pretty useful.

also if u want to save ur data, u can boot using live CD of Ubuntu and access ur windows partition and save the required data elsewhere.

regards

---

### Post by ophilar on 2008-02-24
I tried to use Super Grub USB, and got error 12 after the command usbswitch...
Is there any way to restore the partition table? I can't find the recovery partition yet.

---

