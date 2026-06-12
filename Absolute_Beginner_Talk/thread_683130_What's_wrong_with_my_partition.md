---
title: "What's wrong with my partition?"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2008-01-30
I have consulted a few posts here and there but i can't seem to get everything worked out. I installed Ubuntu server and now it can't boot due to error 17 from Grub

so after typing
"cat /boot/grub/menu.lst" from Supergrub disk that I am booting my machine from right now, 
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
configfile $(grub_device_string)/boot/grub/choose/selecthd.ks t

title findp test
configfile $(grub_device_string)/boot/grub/choose/selectpart. lst
title set SGD variables and boot SGD

configfile $(grub_device_string)/boot/sgd/menu.lst
"

What should I do? I have already wiped out that partition completely and installed ubuntu on from the beginning

Please help me

---

### Post by Scarath on 2008-01-30
You could try:

Try booting from the live CD, open a terminal and go.

```
sudo grub

root (hd0,0)

setup (hd0)

quit


```

This worked for me last time i had a grub error, if this dont work there are lots of grub threads about on the forums.

good luck

---

### Post by dcstar on 2008-01-30
> **disappearedng said:**
> I have consulted a few posts here and there but i can't seem to get everything worked out. I installed Ubuntu server and now it can't boot due to error 17 from Grub

so after typing
"cat /boot/grub/menu.lst" from Supergrub disk that I am booting my machine from right now, 
this is what I get
.......
What should I do? I have already wiped out that partition completely and installed ubuntu on from the beginning

Please help me

Posting what is on a boot disk is totally irrelevant, you need to mount the Ubuntu installation and post the data from that.

[http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub)

---

### Post by disappearedng on 2008-01-30
I went into Supergrub disk GNU linux command line interface 

Grub> find /boot/grub/stage1

Error 15: file not found
What does this mean?

---

