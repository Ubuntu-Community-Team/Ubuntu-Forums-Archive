---
title: "another compaq sound problem thread"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by zakirs on 2007-12-16
hi mine is an compaq v3239 tu laptop with intel hda , cx 20549 codec sound card and intel 945 chipset.........my ubuntu doesnt give me sound and somes times the sound mysteriously re appears after a restart and again the sound dies after another restart.please help i cant live without sound .....also i tried reinstalling alsa and also that intel hda troubleshoot page ....forgot to tell i have gutsy on my laptop :(:(

---

### Post by emitchlpd on 2007-12-16
Hi Zakirs,
Can you post the contents of the following files?

[LIST]
[*]/boot/grub/menu.lst
[*]/etc/modprobe.d/alsa-base
[/LIST]

To do that run:

```

cat /boot/grub/menu.lst

```
(that file extension is dot ell ess tee, or lowercase of LST)

and

```

cat /etc/modprobe.d/alsa-base

```

---

### Post by zakirs on 2007-12-16
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=bcfb9232-bef0-481a-9799-69b50c92c44a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bcfb9232-bef0-481a-9799-69b50c92c44a ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bcfb9232-bef0-481a-9799-69b50c92c44a ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows Vista/Longhorn (loader)
root		(hd0,3)
savedefault
makeactive
chainloader	+1

```




this is out put of  grub/menu.lst

---

### Post by Dave Otter on 2007-12-16
Applicationns-accesories-terminal 

       Type in terminal asoundconf list

    this will tell you soundcards installed

         again type 
                           asoundconf set-default-cardCARD deplcing CARD  with the card you wish to use

---

### Post by zakirs on 2007-12-16
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388


options snd-hda-intel model=hp-laptop

```


i edited that model after seeing ur thread before it was 3stack...


thanks in advance :)

---

### Post by emitchlpd on 2007-12-16
> **zakirs said:**
> ```

options snd-hda-intel model=hp-laptop

```


i edited that model after seeing ur thread before it was 3stack...


thanks in advance :)

I think that last line needs to be "laptop-hp"

```

options snd-hda-intel model=laptop-hp

```

---

### Post by zakirs on 2007-12-16
hi  again no success i edited the file and rebooted ...no succes

Dave ..intel is set as default card

---

### Post by zakirs on 2007-12-16
hi also have gnome alsa mixer installed it shows all are kept to full sound and it shows heading as conexant 20549(venice)

---

### Post by Dave Otter on 2007-12-16
Do you have more than one card installed?

---

### Post by zakirs on 2007-12-16
no dave ,only the inbuilt card which came with the manufacturer

> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


---

### Post by zakirs on 2007-12-16
](*,) [-o<

---

### Post by emitchlpd on 2007-12-16
Zakirs I think that's a different chip than the one I have. I have the NVidia MCP51 so there may be a difference in how the configuration needs to be.

If you're seeing the device in Gnome Mixer then I think the driver is loading properly. I think the thing to focus on is the option you pass the module (driver) in /etc/modprobe.d/alsa-base. "laptop-hp" worked for me. Another one might work for you. 

You can find these options in the Alsa documentation that comes with the driver.

[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)

Look in the "alsa-kernel/Documentation/" folder a file called Alsa-Configuration.txt

---

### Post by zakirs on 2007-12-17
actually the problem is wierd because the sound some time appears mysteriously , like now ican hear my laptop scream....but inkow that after a restart it will be back to good old deaf days even if the model=3stack or odel=hp-laptop please help i cannot live with deaf ubuntu. i even tried reinstalling ubuntu

---

### Post by zakirs on 2007-12-17
hey sucessss yippppeeeeeeeeeeeeeeeeeeeeeee:guitar:\\:D/:-({|==D>

thank you erik this time model=laptop did it for me thanks a lot ;)

---

