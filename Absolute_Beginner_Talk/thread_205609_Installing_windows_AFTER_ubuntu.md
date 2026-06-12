---
title: "Installing windows AFTER ubuntu"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by atomicSpatule on 2006-06-28
Wow... this has incredibly screwed up... I created a NTFS partition with Gparted from the live CD, and I installed windows XP pro on it. Then I rebooted on the live cd and I did the following :
```
sudo grub
root (hd0,0)
setup (hd0)
quit

```
Then I rebooted. It didn't boot. I popped in the live CD and I was able to mount the root partition. But then, I fired Gparted. BAM, my whole hard drive shows as unpartitionned space... It seems my hard drive has no partition table... How in the world am I supposed to fix this?

---

### Post by shoot2kill on 2006-06-28
a quick question, have you got another HDD or partition for the XP install?

---

### Post by newman on 2006-06-28
You can use the windows cd Recovery Console tools to repair the mbr or you can just type fdisk /mbr at the dos prompt>

---

### Post by glotz on 2006-06-28
These articles probably answer your questions
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)

---

### Post by doonium on 2006-06-28
ive rewritten my mbr many times after windows install.  ive always booted the live cd and followed the instructions in the grub manual.  there might be an easier way using a feature of the live cd that i'm unaware of.

---

### Post by njzillest on 2006-06-28
i had same problem for ubuntu 5.05 this is how i did it on that

GO back to the ubuntu installer after windows and ubuntu are both installed. Skip the partitioning and the installation, and just reinstall the Grub. If this doesnt work, Please post your /boot/grub/menu.lst by typing in the command
sudo cat /boot/grub/menu.lst

Hope this helps

---

### Post by atomicSpatule on 2006-06-28
Thanks a lot for the fast replies, the community here is always very helpful :)

---

### Post by atomicSpatule on 2006-06-28
Wow... this has incredibly screwed up... I created a NTFS partition with Gparted from the live CD, and I installed windows XP pro on it. Then I rebooted on the live cd and I did the following :
```
sudo grub
root (hd0,0)
setup (hd0)
quit

```
Then I rebooted. It didn't boot. I popped in the live CD and I was able to mount the root partition. But then, I fired Gparted. BAM, my whole hard drive shows as unpartitionned space... It seems my hard drive has no partition table... How in the world am I supposed to fix this?

---

### Post by atomicSpatule on 2006-06-28
Bump Please help this is insane...
```

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=quiet splash vga=792

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title           Ubuntu, kernel 2.6.15-25-k7
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-25-k7 root=/dev/hda1 ro quiet splash vga=79 2
initrd          /boot/initrd.img-2.6.15-25-k7
savedefault
boot

title           Ubuntu, kernel 2.6.15-25-k7 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-25-k7 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-25-k7
boot

title           Ubuntu, kernel 2.6.15-25-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro quiet splash vga=7 92
initrd          /boot/initrd.img-2.6.15-25-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-25-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash vga=7 92
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash vga=79 2
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by Pavilion on 2006-06-28
[QUOTE=atomicSpatule]Wow... this has incredibly screwed up... I created a NTFS partition with Gparted from the live CD, and I installed windows XP pro on it. Then I rebooted on the live cd and I did the following :
```
sudo grub
root (hd0,0)
setup (hd0)
quit

```
Then I rebooted. It didn't boot. I popped in the live CD and I was able to mount the root partition. But then, I fired Gparted. BAM, my whole hard drive shows as unpartitionned space... It seems my hard drive has no partition table... How in the world am I supposed to fix this?[/QUOTE]

Doesn't XP give an option when loading XP over another OS to keep that OS?  Then doesn't XP install giving additional options?  Anyway, this is what I was told, perhaps I was told wrong.  Anyway, Iv'e not tried it because I'm pure Ubuntu on both machines.:D

---

### Post by atomicSpatule on 2006-06-28
Actually, I don't think so... Anyways, I reinstalled windows XP, and my partition table is back to normal. Now I only need to be able to boot into ubuntu again. Please help

---

### Post by atomicSpatule on 2006-06-28
Finally, after hours of searching google and screwing around, I got it made. How did I do it : Pop in a breezy install cd. Follow instructions, Manual partitioning, configuring mount points, not formatting anything. skipping to installing grub, rebooting

---

### Post by Pavilion on 2006-06-29
[QUOTE=atomicSpatule]Actually, I don't think so... Anyways, I reinstalled windows XP, and my partition table is back to normal. Now I only need to be able to boot into ubuntu again. Please help[/QUOTE]

Well** "Actually, You were right."**  I was curious, and since I was going to upgrade this machine to dapper, I popped in the XP CD and gave it ago.  XP went through all the motions for the install, but when it got to the point where it had to decide where it was going on the hard drive it complained that it didn't reconize the Linux [0X83] partition.  It the gave me the option of deleating the Linux [0X83] partition [Breezy] or exit, I took the exit.  No harm done.  

Thought you might like to know.:)

---

### Post by Pavilion on 2006-06-29
Well** "Actually, You were right."**  I was curious, and since I was going to upgrade this machine to dapper, I popped in the XP CD and gave it ago.  XP went through all the motions for the install, but when it got to the point where it had to decide where it was going on the hard drive it complained that it didn't reconize the Linux [0X83] partition.  It the gave me the option of deleating the Linux [0X83] partition [Breezy] or exit, I took the exit.  No harm done.  

Thought you might like to know.:)

---

