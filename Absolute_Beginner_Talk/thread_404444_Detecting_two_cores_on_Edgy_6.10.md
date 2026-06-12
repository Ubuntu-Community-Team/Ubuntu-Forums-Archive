---
title: "Detecting two cores on Edgy 6.10"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by mand0 on 2007-04-08
Hello,

I know this has been asked often but I am frustrated and I can't seem to find the answers I am looking for.

When I go to System Monitor my computer detects only one core.

Typing in Terminal:

```
uname -a
```

Gives me:

```
2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686 GNU/Linux
```

Typing in Terminal:

```
cat /proc/cpuinfo
```

Gives me:

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 3663.10

```

Now let me explain to you something else.  System Monitor USED to detect two cores BEFORE I installed the beta nvidia drivers following [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29")
guide.  So after I installed the GPU drivers only 1 core is detected. Did my kernel version change during the driver install? Do I have the right kernel version?

Thanks for your help.

---

### Post by hrsetrdr on 2007-04-08
At Grub you should have more than one kernal listed to boot to. Is the SMP kernal listed?

---

### Post by Bachstelze on 2007-04-08
The 386 kernel doesn't have SMP support. The generic one does, do

```
sudo apt-get install linux-image-generic
```

---

### Post by mand0 on 2007-04-08
hrsetrdr, I am not prompted to choose between kernels at boot up.

HymnToLife, this is the output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Bachstelze on 2007-04-08
That's weird, the genric one is installed so you should be prompter for the kernel version you want to start... Could you please paste the contents of /boot/grub/menu.lst ?

---

### Post by mand0 on 2007-04-08
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=9690eee5-aa80-4d68-89a2-815c69482f43 ro
# kopt_2_6=root=/dev/sda1 ro

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
# defoptions=quiet splash

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
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-11-386
boot

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

So I see the two kernel versions listed but I had no idea that I should be getting prompted to choose between them.

---

### Post by Bachstelze on 2007-04-08
I see, the menu is hidden so you should have a message "Press ESC to show menu". Then when the menu appears, choose the generic. Once the system is started, you can remove the 386.

---

### Post by mand0 on 2007-04-08
HymnToLife, you are good! I booted into the generic kernel and I now see both cores. Thank you!

---

### Post by ronocdh on 2007-04-08
I had this same problem. (Thanks, HymnToLife!) In case it's not glaringly obvious, one can edit the /boot/grub/menu.lst and remove the 386 options. That way GRUB'll go straight to the generic kernel, with both cores happily acknowledged. =)

---

### Post by Bachstelze on 2007-04-08
You can also open Synaptic and remove all the packages regarding the 386 kernel since it's not needed. It will also remove the entry in GRUB so the system will boot straight to the generic (since it will be the only one, eh :p).

---

### Post by tommi-fi on 2007-04-11
I use 6.06 LTS and I have dual P3 computer with two 733MHz. What kernel should I use?

---

### Post by Bachstelze on 2007-04-11
```
sudo apt-get install linux-686-smp
```

---

### Post by tommi-fi on 2007-04-12
> **HymnToLife said:**
> ```
sudo apt-get install linux-686-smp
```

And if I upgrade to a 6.10 or 7.04? Was it generic.

---

