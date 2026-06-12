---
title: "Problem in triple booting"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Rabindranath on 2007-11-23
I have XP and ubuntu installed on my system. I installed pclinux os and it seems it uses its own grub. I edited menu.lst ( In pclinuxos ) and I was able to boot into ubuntu but I was not able to see ubuntu loading but a set of codes appearing on the screen. It booted correctly but I think I am not able to shutdown properly too. Could I use the grub of ubuntu to boot into pclinuxos. Can you please tell me the problem in this. 


timeout 20
color black/cyan yellow/cyan
gfxmenu (hd0,9)/usr/share/gfxboot/themes/pclinuxos/boot/message
default 0

title pclinuxos
kernel (hd0,9)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sda10  acpi=on splash=silent vga=788
initrd (hd0,9)/boot/initrd.img

title linux-nonfb
kernel (hd0,9)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/sda10  acpi=on
initrd (hd0,9)/boot/initrd.img

title failsafe
kernel (hd0,9)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/sda10  failsafe acpi=on
initrd (hd0,9)/boot/initrd.img

title ubuntu
kernel (hd0,8)/boot/vmlinuz-2.6.22-14-generic BOOT_IMAGE=ubuntu root=/dev/sda9
initrd (hd0,8)/boot/initrd.img-2.6.22-14-generic

title windows
root (hd0,0)
makeactive
chainloader +1


Thanks for your replies.

---

### Post by meierfra on 2007-11-23
You can solve the problem by just copy and pasting the ubuntu title from your ubuntu menu.lst to the PCLinuxOS menu.lst  ( that way you will have the correct boot parameters)

But I recommend one of the following two methods instead

1) Use this for ubuntu in the  PCLinuxOS menu.lst:

title Ubuntu
root (hd0,8 )
configfile /boot/grub/menu.lst

(there really shouldn't be a space between 8 and ). But I avoided the smiley face)

If you choose Ubuntu from the grub-menu, this will bring up the Ubuntu grub-menu.
I  prefer the "configfile" method since you won't have to manually update "menu.lst" after kernel upgrades.
You might want to use "timeout 1"  and "hiddenmenu" in the Ubuntu menu.lst( (Then you won't hardly notice that there is a second grub-menu envolved.)

2)  Reinstall the Ubuntu-grub to the MBR by typing 

sudo grub
root (hd0,8 ) 
setup (hd0)
quit

in a terminal
Then  add PCLinuxOS to the ubuntu grub-menu:

title PCLinuxPS
root (hd0,9)
configfile /boot/grub/menu.lst

---

### Post by kellemes on 2007-11-23
> **meierfra said:**
> You can solve the problem by just copy and pasting the ubuntu title from your ubuntu menu.lst to the PCLinuxOS menu.lst  ( that way you will have the correct boot parameters)

But I recommend one of the following two methods instead

1) Use this for ubuntu in the  PCLinuxOS menu.lst:

title Ubuntu
root (hd0,8 )
configfile /boot/grub/menu.lst

(there really shouldn't be a space between 8 and ). But I avoided the smiley face)

If you choose Ubuntu from the grub-menu, this will bring up the Ubuntu grub-menu.
I  prefer the "configfile" method since you won't have to manually update "menu.lst" after kernel upgrades.
You might want to use "timeout 1"  and "hiddenmenu" in the Ubuntu menu.lst( (Then you won't hardly notice that there is a second grub-menu envolved.)

2)  Reinstall the Ubuntu-grub to the MBR by typing 

sudo grub
root (hd0,8 ) 
setup (hd0)
quit

in a terminal
Then  add PCLinuxOS to the ubuntu grub-menu:

title PCLinuxPS
root (hd0,9)
configfile /boot/grub/menu.lst

+1
The "configfile-method" is the way to go..

Download/burn Super Grub Disk for when you get into trouble.. it is able to perform magic on bootloader-related stuff.

---

