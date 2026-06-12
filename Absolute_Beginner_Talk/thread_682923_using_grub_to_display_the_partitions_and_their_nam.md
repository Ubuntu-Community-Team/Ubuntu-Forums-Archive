---
title: "using grub to display the partitions and their names"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2008-01-30
Hi
I am trying to use the super grub cd and restore my grub. 
How do i display my devices (I can't log in to my ubuntu partition and i deleted my windows partition) like
" partition 1   (hd0....) .... etc"
and what are the commands for me to execute to restore my ubuntu partition in the grub loader menu??
Please help me

---

### Post by Fixman on 2008-01-30
Do
```
 cat /boot/grub/menu.lst 
```
And post the results.

---

### Post by dstew on 2008-01-30
From the grub command prompt, type```
root (
```
followed by a <TAB>, and GRUB will display the list of drives, partitions, or file names. This is a direct paste from the [Gnu GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html#Interface").

---

### Post by disappearedng on 2008-01-30
so after typing 
"cat /boot/grub/menu.lst"
this is what I get
"
default 2
timeout 2
setgrubdevice # this is compulsory
#gfxmenu /boot/grub/message
foreground ffffff
background 0c00ff
color white/brown yellow /cyan

title incio normal / normal boot
kernel $(grub_device)/vmlinuz lang=es ally=none root =/dev/ram0 ramdisk_size 100000 initrd=initramfs quiet BOOT=live splash
initrd $(grub_device)/initramfs

title Soporte de accesibilidad / accessibility support --> 
configfile $(grub_device)/boot/sgd/menu.lst

title Normal boot. Kernel is aware of boot device
kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash boot_device=$(grub_device)

#the two commands: setgrubdevice and usbshift are needed
# so that SGD works well
usbshift
configfile #(grub_device)/boot/sgd/menu.lst

title Normal boot. Kernel is aware of boot device
kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash boot_device=$(grub_device) initrd $(grub_device)/initramfs

title Normal boot. Selecting kernel and initrd files depending on grub_device 
kernel $(grub_device)/vmlinuz_$(grub_device_string) lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash boot_device=$(grub_device) initrd $(grub_device)/initramfs_$(grub_device_string)

title Selecthd test
configfile $(grub_device_string)/boot/grub/choose/selecthd.kst

title findp test
configfile $(grub_device_string)/boot/grub/choose/selectpart.lst
title set SGD variables and boot SGD

configfile $(grub_device_string)/boot/sgd/menu.lst
"

What do I do from now on?

---

### Post by NeoGreen on 2008-01-30
Check these links out [http://www.sorgonet.com/linux/grubrestore/]("http://www.sorgonet.com/linux/grubrestore/") and this one [http://www.sorgonet.com/linux/grubrestore/]("http://www.sorgonet.com/linux/grubrestore/") If you are trying to restore Grub.

---

### Post by bodhi.zazen on 2008-01-30
use tab completion as suggested by dstew

See this link as well : [uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

