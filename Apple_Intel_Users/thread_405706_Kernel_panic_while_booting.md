---
title: "Kernel panic while booting"
date: 2007-04-10
forum: Apple Intel Users
---

### Post by lorentsenjr on 2007-04-10
hi.

im running ubuntu on my macbook (1,83 ghz) and it is all great :) (tho my right click button sometimes stops working, but i just write the commad, and take a quick restart, and that is fixed)

there is only one thing that doesnt work properly, and thats the booting, about half of the time it panics, and i got to restart, i am very new to linux systems, but i have figured out that i have to put "lpj=7330000" into my /boot/grub/menu.lst file, but i cant seem to get anymore information, so where exactly should i type it? 

(and yes, i forgot to type it during innstallation - as for other information, if needed, i run edgy)

---

### Post by Azathoth_ on 2007-04-10
You have to type it in the instruction of the boot, i mean, in:

> title           Ubuntu, kernel 2.6.20-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-14-generic root=/dev/sda3 lpj=7330000 ro quiet splash vga=792
initrd          /boot/initrd.img-2.6.20-14-generic
quiet
savedefault

As you see in kernel (don´t mind the exact position) and you have to put it always when you install a new kernel

---

### Post by cyberdork33 on 2007-04-10
one of the options in the automagic kernels list can be edited to append the line to any new kernel when it is added to the list. I can't remember the option name off the top of my head...

EDIT: Found it:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```
Just add "lpj=7330000" (without quotes) to the defoptions line so it will look like this:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash lpj=7330000
```
Probably should add it to your alternative kernels too just below that:
```
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single lpj=7330000
```

---

### Post by Azathoth_ on 2007-04-10
> **cyberdork33 said:**
> one of the options in the automagic kernels list can be edited to append the line to any new kernel when it is added to the list. I can't remember the option name off the top of my head...

EDIT: Found it:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```
Just add "lpj=7330000" (without quotes) to the defoptions line so it will look like this:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash lpj=7330000
```
Probably should add it to your alternative kernels too just below that:
```
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single lpj=7330000
```

I think, in this situation you have to uncomment altoption or defoptions

---

### Post by cyberdork33 on 2007-04-10
NO DO NOT UNCOMMENT: This is important! Double ## are completely commented out. Single # are commented out to grub but not the update script.

Here is the entire options list:
```
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
# kopt=root=UUID=baa37e81-47be-4d07-bbda-2db4cf22e94e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
# defoptions=quiet vga=795 splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##
```

---

### Post by Azathoth_ on 2007-04-11
Thanks, i didn't know

---

