---
title: "3 min and 36 sec to boot!"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by Freddd on 2005-11-26
I installed ubuntu on a 20 gb hard disc for about four days ago, and everything worked fine:
* The booting time was ok
* The splash screen was shown during the booting process

Yesterday, I removed my 20 gb hard disc because it was old (5 year) and to small. I bought a new hitachi 80 gb hard disc and replaced it with the old one. I installed ubuntu and the installation progress did just go fine. I didn't expect to get any problems but I did, and I have reinstalled ubuntus 3 times.

The problems that I'm now having:
* It takes 3 minutes and 36 seconds to boot!!
* The splash screen is displayed at the beginning (just a few seconds) but then disappears.

I'm kind of thinking this problem is related to my har disc. I used the default partioning that ubuntus suggest. I get an extra partition for swapping, about 1 gb.

Does anyone know how to solve this problem? From what I know I don't think I'm getting any error message when booting.

---

### Post by Kvark on 2005-11-26
When you boot up, look at the text, is there a particular line that it stays at for a very long time?

---

### Post by deNoobius on 2005-11-26
Same thing happened to me (worse) when I started Ubuntu, and I traced it to a non-working CD drive that was still plugged into the system.  I removed it and all was fine.  What I'm trying to say-- make sure the power and data connections to the HD are solid.

---

### Post by Freddd on 2005-11-26
Here is what happens

1. Uncompressing Linux... ok booting the kernel

2. Splash screen - Loading modules freezes for some time

3. Back to step 1 and now for a very long time

4. The modules are loading and all of them seems to be loaded normaly (no splash screen)

Here is the message I get at step 1 and 3 (maybe nothing worth readin?)

> 
root(hd 0,0)
Filesystem type is ext2fs, partition type 0X83
Kernel /boot/vmlinuz-2.6.12-10-306 root = 
dev/hda1 ro quiet splash
[Linux-bzimage, setup = ox 1c00, size 0X50ce59 bytes]
Save default
boot
uncompressing Linux... Ok, booting the kernel
Loading, please wait...


I didn't do any physical settings on the hard disc when I installed it, only connected the power and the data cable.
The computer I'm using is pretty old, as old as my 20 gb hard disc in other wors 5 year, don't know if that might be the case.

---

### Post by paulozzzz on 2005-11-26
It is probable that the DMA has been disabled after the change.

I will leave to the experts as to how enable DMA for HDs/CD-ROMs in Linux.

---

### Post by Freddd on 2005-11-26
Hmm okey? If it is the dma and it can be solved then I'm happy.

I have checked the cables to my disc, pluged out and pluged in, I still have the problem though. I would be extremly happy if anyone can help me out here, I do really want to us ubuntu and say good bye to windows.

---

### Post by paulozzzz on 2005-11-26
[QUOTE=Freddd]Hmm okey? If it is the dma and it can be solved then I'm happy.

I have checked the cables to my disc, pluged out and pluged in, I still have the problem though. I would be extremly happy if anyone can help me out here, I do really want to us ubuntu and say good bye to windows.[/QUOTE]

Unfortunatelly I can not help you beyond saying it is disabled DMA support since I am also new to Linux.  Perhaps it is useful if you start another thread called "How do I enable DMA" or something like that.

---

### Post by kosmic on 2005-11-26
to enable dma, go to a console and do :
 
sudo hdparm -d1 /dev/hda1 if your hard drive is hda1

---

### Post by Freddd on 2005-11-26
How do I know what hda-number my disc have?

I tried your code but I get:
> 
/dev/hda1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Invalid argument
 using_dma    =  0 (off)


I have used automatix on my previous installations. Will any of the changes be saved when making a new installation of ubuntu? I wonder because maybe automatix is responsible for these troubles. No offence author, just trying to figure out the reason of my problems. I wont use automatix on the installation I'm using now though.

---

### Post by tseliot on 2005-11-26
[QUOTE=Freddd]How do I know what hda-number my disc have?

I tried your code but I get:


I have used automatix on my previous installations. Will any of the changes be saved when making a new installation of ubuntu? I wonder because maybe automatix is responsible for these troubles. No offence author, just trying to figure out the reason of my problems. I wont use automatix on the installation I'm using now though.[/QUOTE]

Automatix can't damage anything because it just modifies your /etc/hdparm.conf

If you want to see that file:

```
sudo gedit /etc/hdparm.conf
```

Please post the content of this file

EDIT: Post also the output of this command:
```
[COLOR="Red"]sudo sfdisk -l[/COLOR]
```

and of this other one:
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Freddd on 2005-11-26
Thanks for the reply, here is the file:

> 
## This is the default configuration for hdparm for Debian.  It is a 
## rather simple script, so please follow the following guidelines :)
## Any line that begins with a comment is ignored - add as many as you 
## like.  Note that an in-line comment is not supported.  If a line 
## consists of whitespace only (tabs, spaces, carriage return), it will be
## ignored, so you can space control fields as you like.  ANYTHING ELSE
## IS PARSED!!  This means that lines with stray characters or lines that 
## use non # comment characters will be interpreted by the initscript.  
## This has probably minor, but potentially serious, side effects for your 
## hard drives, so please follow the guidelines.  Patches to improve 
## flexibilty welcome.  Please read /usr/share/doc/hdparm/README.Debian for 
## notes about known issues, especially if you have an MD array.
##
## Note that if the init script causes boot problems, you can pass 'nohdparm' 
## on the kernel command line, and the script will not be run.
##
## Uncommenting the options below will cause them to be added to the DEFAULT
## string which is prepended to options listed in the blocks below.
##
## If an option is listed twice, the second instance replaces the first.
##
## /sbin/hdparm is not run unless a block of the form:
##      DEV {
##         option
##         option
##         ...
##      }
## exists.  This blocks will cause /sbin/hdparm OPTIONS DEV to be run.
## Where OPTIONS is the concatenation of all options previously defined
## outside of a block and all options defined with in the block.

# -q be quiet
quiet 
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
#apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
#dma = off
# -D enable/disable the on-drive defect management
#defect_mana = off
# -E cdrom speed
#cd_speed = 16
# -k disable/enable the "keep_settings_over_reset" flag for this drive
#keep_settings_over_reset = off
# -K disable/enable the drive's "keep_features_over_reset" flag
#keep_features_over_reset = on
# -m sector count for multiple sector I/O
#mult_sect_io = 32
# -P maximum sector count for the drive's internal prefetch mechanism
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode

# Root file systems.  Please see README.Debian for details
# ROOTFS = /dev/hda

## New note - you can use straight hdparm commands in this config file 
## as well - the set up is ugly, but it keeps backwards compatibility
## Additionally, it should be noted that any blocks that begin with 
## the keyword 'command_line' are not run until after the root filesystem
## is mounted.  This is done to avoid running blocks twice.  If you need 
## to run hdparm to set parameters for your root disk, please use the 
## standard format.

#Samples follow:
#First three are good for devfs systems, fourth one for systems that do 
#not use devfs.  The fifth example uses straight hdparm command line
#syntax.  Any of the blocks that use command line syntax must begin with
#the keyword 'command_line', and no attempt is made to validate syntax.  
#It is provided for those more comfortable with hdparm syntax. 

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}
/dev/cdrom {
       dma = on
}



Here is the output of the other file: 
> 
Disk /dev/hda: 10011 cylinders, 255 heads, 63 sectors/tracks
Devices = cylinders with 8225280 byte, block with 1024 byte, counter from 0

   Device Start Beginning   End     Cyl.     Block   Id  System
/dev/hda1   *      0+   9870    9871-  79288776   83  Linux
/dev/hda2       9871   10010     140    1124550    5  Extended
/dev/hda3          0       -       0          0    0  Empty
/dev/hda4          0       -       0          0    0  Empty
/dev/hda5       9871+  10010     140-   1124518+  82  Linux v&#228;xling / Solaris


Got that output in Swedish. Did my best to translate it to English ;)

---

### Post by tseliot on 2005-11-26
what's the output of this:
sudo gedit /boot/grub/menu.lst

---

### Post by paulozzzz on 2005-11-26
Verify the BIOS setup if there is a DMA enable option.  In PCChips mobos DMA support must be enabled via BIOS setup.

---

### Post by Freddd on 2005-11-26
Output of: sudo gedit /boot/grub/menu.lst

> 
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST



[QUOTE=paulozzzz]Verify the BIOS setup if there is a DMA enable option.  In PCChips mobos DMA support must be enabled via BIOS setup.[/QUOTE]
Okey, gonna check that also.

---

### Post by tseliot on 2005-11-26
I hope you find the answer in the bios.
If it's not so, post the output of:

```
lspci
```

and

```
lsmod
```

---

### Post by Freddd on 2005-11-26
I did look in Bios but I couldn't find any setting for "enable DMA". Not quit sure where to look in but I tried to read all sections and settings. 

Here is the output of the other commands:

lspci

> 
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8605 [ProSavage PM133] (rev 0 1)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8605 [PM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (r ev 22)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 10)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 10)
0000:00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 A udio Controller (rev 20)
0000:00:12.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Inter face
0000:01:00.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pr o] (rev a3)


lsmod
> 
Module                  Size  Used by
nls_cp437               5888  1
isofs                  32824  1
udf                    75524  0
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
acx_pci               122752  0
firmware_class          9472  1 acx_pci
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            25792  1
gameport               14472  1 snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_seq,snd_pcm
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
snd_rawmidi            22816  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    48644  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd
i2c_viapro              7696  0
via686a                17816  0
i2c_sensor              3456  1 via686a
i2c_core               19728  4 i2c_acpi_ec,i2c_viapro,via686a,i2c_sensor
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
via_agp                 9472  1
agpgart                32328  1 via_agp
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
piix                    9476  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
uhci_hcd               28048  0
usbcore               104316  2 uhci_hcd
ide_cd                 36996  1
cdrom                  33952  1 ide_cd
ide_disk               16128  3
ide_generic             1664  0
via82cxxx              12188  1
ide_core              125268  5 piix,ide_cd,ide_disk,ide_generic,via82cxxx
unix                   24624  608
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon


---

### Post by Freddd on 2005-11-26
No clue? :(

Your help is very much appreciated.

---

### Post by tseliot on 2005-11-26
[QUOTE=Freddd]I did look in Bios but I couldn't find any setting for "enable DMA". Not quit sure where to look in but I tried to read all sections and settings. 

Here is the output of the other commands:

lspci



lsmod[/QUOTE]
Try this:
sudo gedit /etc/modules

and post it

---

### Post by Freddd on 2005-11-26
This is what I get

> 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
piix
ide-core
ide-cd
ide-disk
ide-generic


---

### Post by tseliot on 2005-11-26
[QUOTE=Freddd]I tried it but I get:[/QUOTE]
Comment out ide-disk and ide-generic like in the example:

lp
mousedev
psmouse
piix
ide-core
ide-cd
[COLOR="Red"]#ide-disk
#ide-generic[/COLOR]

Save and exit

Then restart your computer and try to enable DMA again

---

### Post by Freddd on 2005-11-26
Okey, try to enable it in BIOS or? Because I can't find that alternative.

---

### Post by tseliot on 2005-11-26
[QUOTE=Freddd]Okey, try to enable it in BIOS or? Because I can't find that alternative.[/QUOTE]
I mean, restart your computer.
Then (after it has booted) type this command:

sudo hdparm -d1 /dev/hda

and post the output

---

### Post by Freddd on 2005-11-26
Here is the output
> 
/dev/hda:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)


---

### Post by farmer on 2005-11-26
Congratulations. DMA is on.

---

### Post by tseliot on 2005-11-26
[QUOTE=Freddd]Here is the output[/QUOTE]
Ok now DMA is activated.

1) Did last boot take the same time as before (3 min and 36 sec)?

[COLOR="Red"]If the answer is yes, type:[/COLOR]

```
sudo gedit /etc/hdparm.conf
```


and add this at the end of the file:
```
/dev/hda {
dma = on
}
```

and restart your computer

---

### Post by Freddd on 2005-11-26
sorry, gonna read your post above first.

---

### Post by Freddd on 2005-11-26
I did as you said but I still can't see any difference. I restarted the computer after following those two steps but it's still the same :confused:

The file after editing as instructed:
> 
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode

# Root file systems.  Please see README.Debian for details
# ROOTFS = /dev/hda

## New note - you can use straight hdparm commands in this config file 
## as well - the set up is ugly, but it keeps backwards compatibility
## Additionally, it should be noted that any blocks that begin with 
## the keyword 'command_line' are not run until after the root filesystem
## is mounted.  This is done to avoid running blocks twice.  If you need 
## to run hdparm to set parameters for your root disk, please use the 
## standard format.

#Samples follow:
#First three are good for devfs systems, fourth one for systems that do 
#not use devfs.  The fifth example uses straight hdparm command line
#syntax.  Any of the blocks that use command line syntax must begin with
#the keyword 'command_line', and no attempt is made to validate syntax.  
#It is provided for those more comfortable with hdparm syntax. 

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}
/dev/cdrom {
       dma = on
}

/dev/hda:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)


---

### Post by tseliot on 2005-11-26
[QUOTE=Freddd]I did as you said but I still can't see any difference. I restarted the computer after following those two steps but it's still the same :confused:

The file after editing as instructed:[/QUOTE]
In your hdparm.conf there should be this:

```
/dev/hda {
dma = on
}
```

instead of 

```
/dev/hda:
setting using_dma to 1 (on)
using_dma = 1 (on)
```

Trust me.

---

### Post by Freddd on 2005-11-26
Sorry my fault and I trust you :)

I changed it and restarted. Still no difference though. :(

---

### Post by tseliot on 2005-11-26
[QUOTE=Freddd]Sorry my fault and I trust you :)

I changed it and restarted. Still no difference though. :([/QUOTE]

Type this exact command:

sudo hdparm -d /dev/hda

(not sudo hdparm -d1 /dev/hda)

and post the output

---

### Post by Freddd on 2005-11-26
There you go:

> 
/dev/hda:
 using_dma    =  0 (off)


---

### Post by tseliot on 2005-11-26
[QUOTE=Freddd]There you go:[/QUOTE]
Ok, perhaps this will fix it:

sudo gedit /etc/modules

and make it look like this:

```
via82cxxx
lp
mousedev
psmouse
piix
ide-core
ide-cd
ide-disk
ide-generic
```

Save and exit.

Restart your computer

After it boots: 

sudo hdparm -d /dev/hda

and post the output again

I'm going to bed. Good night. (I'll answer tomorrow)

---

### Post by Freddd on 2005-11-26
Booting time still the same and here is the output

> /dev/hda:
 using_dma    =  0 (off)


Thank you for helping me.

---

### Post by tseliot on 2005-11-27
[QUOTE=Freddd]Booting time still the same and here is the output



Thank you for helping me.[/QUOTE]
You're welcome :) .

Could you tell me the model of your motherboard?

---

### Post by Freddd on 2005-11-27
Of course. It's an old computer what's the easiest way to find out the type of my motherboard?

I measured the booting time today: 4 minutes and 37 seconds :(

---

### Post by Freddd on 2005-11-27
I looked inside the computer and here is what I found:

> 
VIA VT82C686A


---

### Post by Freddd on 2005-11-27
No clue tseliot? Please tell me if there is anything more I can do.

---

### Post by Freddd on 2005-11-27
I changed back to my original harddrive just to double check that it works as intended and it does. Loading time is normal and the splash screen is shown.
My problem has something to do with my hard drive.

Can it possibly be something about my motherboard or bios? Maybe it doesn't support an 80 gb disc?

---

### Post by tseliot on 2005-11-27
[QUOTE=Freddd]No clue tseliot? Please tell me if there is anything more I can do.[/QUOTE]
Try this:
Keep your /etc/modules as I told you yesterday.
 
sudo gedit /etc/hotplug/blacklist

and add via82cxxx at the end of the file

Restart your computer and tell me if anything has changed.

If it doesn't work I have another trick

[QUOTE=Freddd]Can it possibly be something about my motherboard or bios? Maybe it doesn't support an 80 gb disc?[/QUOTE]
I think it's just a matter of modules which are not loaded for reasons I can't understand.

---

### Post by tseliot on 2005-11-27
Don't give in, we can make it work

---

### Post by Freddd on 2005-11-27
Thanks for cheering me up :)

I did the blacklist thing but it's still the same. I measured the booting time to be sure.

---

### Post by tseliot on 2005-11-27
[QUOTE=Freddd]Thanks for cheering me up :)

I did the blacklist thing but it's still the same. I measured the booting time to be sure.[/QUOTE]

Ok try this other trick:

```
sudo gedit /etc/modules
```

and add amd74xx at the end.

Then:

```
sudo gedit /etc/hotplug/blacklist
```

and add amd74xx at the end.

Restart your computer

---

### Post by Freddd on 2005-11-27
I'm sorry to say it but it is still no difference :(

My etc/modules contains both via82cxxx and amd74xx. The same goes for the blacklist, is that okey?

---

### Post by tseliot on 2005-11-27
Do you manage to enable DMA manually?

sudo hdparm -d /dev/hda

and post the output

sudo hdparm -d1 /dev/hda

and post the output

---

### Post by Freddd on 2005-11-27
I can't find any option in bios to enable DMA.

Here is the output of sudo hdparm -d /dev/hda
> 
/dev/hda:
 using_dma    =  0 (off)


And the other one:
> 
/dev/hda:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)


---

### Post by tseliot on 2005-11-27
[QUOTE=Freddd]I can't find any option in bios to enable DMA.

Here is the output of sudo hdparm -d /dev/hda


And the other one:[/QUOTE]

Ok, remove via82cxxx and amd74xx from etc/modules and /etc/hotplug/blacklist

then do this:

uname -r

and post the output

I need to know that you  have more than 1 kernel to boot in just in case anything goes wrong.

---

### Post by Freddd on 2005-11-27
I removed both via and amd from the files and the executed the command, without doing a restart, hope that was correct.

Output of uname -r
> 
2.6.12-10-386


---

### Post by tseliot on 2005-11-27
[QUOTE=Freddd]I removed both via and amd from the files and the executed the command, without doing a restart, hope that was correct.

Output of uname -r[/QUOTE]
I suppose you have a k7 CPU:

sudo apt-get install linux-k7

When it finishes installing do:

sudo gedit /boot/config-2.6.12-10-k7

Then look for this line (use the search function in the text editor): 

CONFIG_BLK_DEV_VIA82CXXX=m

and change it to:

CONFIG_BLK_DEV_VIA82CXXX=y

save and exit.

Restart your computer (it will boot in your new kernel).

NOTE: if your computer can boot or have other problems you have to:

Turn on your computer
Keep pressing ESC as soon as you have turned it on (during the bootstrap)
Until you the Grub menu shows up
Choose your previous kernel (2.6.12-i386)
And it will boot

---

### Post by Freddd on 2005-11-27
The computer boots with no problem except the long booting time ;)
4 min and 36 seconds.

This is very strange, I do really wonder why this happens...

---

### Post by tseliot on 2005-11-27
[QUOTE=Freddd]The computer boots with no problem except the long booting time ;)
4 min and 36 seconds.

This is very strange, I do really wonder why this happens...[/QUOTE]
Yep, it's weird. I have to find another solution then. I hope some googling enlightens my mind ;)

---

### Post by Freddd on 2005-11-27
Okey, thank you very much for taking time to help me. I will try to google too. :???:

---

### Post by tseliot on 2005-11-27
BTW is DMA disabled even if it is enabled in your hdparm.conf.
Please check it

I have to go for launch. Catch ya later.

---

### Post by Freddd on 2005-11-27
Sorry but I don't remember how to check that :confused:

---

### Post by paulozzzz on 2005-11-27
I am sorry I can not help you as I am a Linux newbie too.

I am almost sure it is a DMA problem because I had HD sluguishness in Windows.  But in that case enabling it in BIOS was enough.:(

---

### Post by paulozzzz on 2005-11-27
Judging by your boot menu, it seems you have other kernels in your system.  Does the problem occur when you boot up with those older kernels?

---

### Post by Freddd on 2005-11-27
The problems occur in every case with the new hard disc. Everything works fine with the old one, how come there is no DMA problem with that one then? :confused:

---

### Post by Freddd on 2005-11-27
I have been looking in Bios again and the only option for DNA I can find is by going to the menu "PCI /Plug And Play Setup":

> 
DMA Channel 0
DMA Channel 1
DMA Channel 3
DMA Channel 5
DMA Channel 6
DMA Channel 7


The settings I can change here is either PnP or ISA/EISA
As it is now all channels have the setting PnP.

---

### Post by tseliot on 2005-11-27
[QUOTE=Freddd]Sorry but I don't remember how to check that :confused:[/QUOTE]
sudo gedit /etc/hdparm.conf

---

### Post by Freddd on 2005-11-27
Output

> 
## This is the default configuration for hdparm for Debian.  It is a 
## rather simple script, so please follow the following guidelines :)
## Any line that begins with a comment is ignored - add as many as you 
## like.  Note that an in-line comment is not supported.  If a line 
## consists of whitespace only (tabs, spaces, carriage return), it will be
## ignored, so you can space control fields as you like.  ANYTHING ELSE
## IS PARSED!!  This means that lines with stray characters or lines that 
## use non # comment characters will be interpreted by the initscript.  
## This has probably minor, but potentially serious, side effects for your 
## hard drives, so please follow the guidelines.  Patches to improve 
## flexibilty welcome.  Please read /usr/share/doc/hdparm/README.Debian for 
## notes about known issues, especially if you have an MD array.
##
## Note that if the init script causes boot problems, you can pass 'nohdparm' 
## on the kernel command line, and the script will not be run.
##
## Uncommenting the options below will cause them to be added to the DEFAULT
## string which is prepended to options listed in the blocks below.
##
## If an option is listed twice, the second instance replaces the first.
##
## /sbin/hdparm is not run unless a block of the form:
##      DEV {
##         option
##         option
##         ...
##      }
## exists.  This blocks will cause /sbin/hdparm OPTIONS DEV to be run.
## Where OPTIONS is the concatenation of all options previously defined
## outside of a block and all options defined with in the block.

# -q be quiet
quiet 
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
#apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
#dma = off
# -D enable/disable the on-drive defect management
#defect_mana = off
# -E cdrom speed
#cd_speed = 16
# -k disable/enable the "keep_settings_over_reset" flag for this drive
#keep_settings_over_reset = off
# -K disable/enable the drive's "keep_features_over_reset" flag
#keep_features_over_reset = on
# -m sector count for multiple sector I/O
#mult_sect_io = 32
# -P maximum sector count for the drive's internal prefetch mechanism
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode

# Root file systems.  Please see README.Debian for details
# ROOTFS = /dev/hda

## New note - you can use straight hdparm commands in this config file 
## as well - the set up is ugly, but it keeps backwards compatibility
## Additionally, it should be noted that any blocks that begin with 
## the keyword 'command_line' are not run until after the root filesystem
## is mounted.  This is done to avoid running blocks twice.  If you need 
## to run hdparm to set parameters for your root disk, please use the 
## standard format.

#Samples follow:
#First three are good for devfs systems, fourth one for systems that do 
#not use devfs.  The fifth example uses straight hdparm command line
#syntax.  Any of the blocks that use command line syntax must begin with
#the keyword 'command_line', and no attempt is made to validate syntax.  
#It is provided for those more comfortable with hdparm syntax. 

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}
/dev/cdrom {
       dma = on
}

/dev/hda {
dma = on
}


---

### Post by tseliot on 2005-11-27
[QUOTE=Freddd]Output[/QUOTE]

Can you try to put the harddisk in another PC and install Ubuntu there? In this way we can see if the problem is related to the harddisk or to your motherboard. You can also try to change the cable of the drive.

OR give a better look at your Bios and look for anything related to IDE devices

ANOTHER THING: post the output of:

[COLOR="Red"]```
cat /proc/ide/ide0/hda/model
```[/COLOR]

---

### Post by Freddd on 2005-11-27
[QUOTE=tseliot]Can you try to put the harddisk in another PC and install Ubuntu there? In this way we can see if the problem is related to the harddisk or to your motherboard. You can also try to change the cable of the drive.

OR give a better look at your Bios and look for anything related to IDE devices[/QUOTE]

I wish I could try that, maybe later this week. 

Since my computer is 5 years old and so is the bios can't that be a possible reason? Maybe the old version of bios doesn't support an 80 gb disc?

I looked on my disc where the data cable shall be plugged and it's seem that a one of all the little pins are bended.  The pin is very much bended and think that one wont be connected to the data cable when I plug it in. Can that possibly be a reason for all this troubles? Everything with the disc seems to work okey except the booting time.

Output of cat /proc/ide/ide0/hda/model
> 
HDS728080PLAT20


---

### Post by paulozzzz on 2005-11-27
"You can also try to change the cable of the drive."

Good idea.  Are you using the flat cable designed for high performance drives?  These differ from the common ones by a ground wire alternating with data wires intended to eliminate crosstalk between the data lines with greater bandwidth.  The crosstalk can ruin the performance of your system by introducing too much data errors.

You can easily recognize the high bandwidth flat cable as it has twice the number of wires the common cable has.

---

### Post by tseliot on 2005-11-27
Incredible, look at this [http://www.infos-du-net.com/forum/121489-6-probleme-rame-bizzare-quot]("http://www.infos-du-net.com/forum/121489-6-probleme-rame-bizzare-quot")

This French user has the same problem with DMA in Windows (with your hard drive).

I suspect there's something wrong with your hard disk or it's just an obsolete BIOS of the motherboard

---

### Post by Freddd on 2005-11-27
I'm thinking of returning the hard drive to where I bought it and buy another one. Seems to be the easiest solution. But maybe I shall try to update my BIOS first?

Is there any easy way to update BIOS?

> 
Bios is: Megatrends AMIBIOS
Motherboard: VIA VT82C686A


I have been googleing around but I don't know where to find what I need. I guess I have make a boot disc to flash my bios?

I looked at the url you posted but my knowledge of French is very limited ;)

---

### Post by tseliot on 2005-11-27
[QUOTE=Freddd]I'm thinking of returning the hard drive to where I bought it and buy another one. Seems to be the easiest solution. But maybe I shall try to update my BIOS first?

Is there any easy way to update BIOS?



I have been googleing around but I don't know where to find what I need. I guess I have make a boot disc to flash my bios?

I looked at the url you posted but my knowledge of French is very limited ;)[/QUOTE]
I have no idea of how to update your bios.

Check that  you are using an 80-thread Ultra ATA/66-cable

If you are using it, then bring the hard drive back to the shop. I can recommend you Maxtor harddisks because I've got 4 different models and they are very good and reliable.

---

### Post by KompresZor on 2005-11-27
Freddd, did you set the master/slave jumpers properly on the new HD? A miss-configured HD will cause very long boot times.

---

### Post by Freddd on 2005-11-27
I have not changed the configuration of the hd. I thought they were configured to work by default? Hmm what setting shall I have if this is the only disc I use?

---

### Post by KompresZor on 2005-11-27
If it's just a single drive either "master" or "single" will work. Some come jumpered as master, but mostly they come set as a slave so you can add it as a second drive in the chain.

---

### Post by Freddd on 2005-11-27
I have checked it now and it is set as Device 0 (MASTER).

---

### Post by Freddd on 2005-11-27
This is how my cable looks like (sorry for bad quality):

[IMG]http://www.plump.se/100_1011.jpg[/IMG]

Do I have the right type of cable?

If I have the right type of cable then I will return my hard disc and buy another kind. Is there any easy way for me to remove all data ie the ubuntus installation. I want the disc to be empty if I'm going to return it.

If I'm not having the right type of cable I will buy the correct one, which is?

---

### Post by paulozzzz on 2005-11-27
[QUOTE=Freddd]This is how my cable looks like (sorry for bad quality):

Do I have the right type of cable?

If I have the right type of cable then I will return my hard disc and buy another kind. Is there any easy way for me to remove all data ie the ubuntus installation. I want the disc to be empty if I'm going to return it.

If I'm not having the right type of cable I will buy the correct one, which is?[/QUOTE]

Does you camera feature a macro or close up lens setup?  It is too out of focus to judge.

---

### Post by KompresZor on 2005-11-27
Then I'll have to go with tesliot's suggestion, take it back and get a new drive. I've never had much luck with hitachi drives or western digital. But all the Maxtor drives I've had run like a fine watch :)

EDIT: wow! you guys are fast posters ;-)

I think that is a 40 pin cable, as most 80 pins cables have a blue connector. But the drive should be backward compatible and be at least as fast as the old drive.

---

### Post by tseliot on 2005-11-27
I can't recognise the cable in this way. Can you see any writings on the cable?

BTW a common (RECENT) cable is an ATA 100 or ATA 133, however a common ATA 66 cable will be fine as your motherboard is likely not to support anything higher than DMA 66.

---

### Post by Freddd on 2005-11-27
The end of the cable connected to the motherboard(?) is blue

The writings of the cable says:

> 
HCM 23129 RJ AWM STYLE 2678 30 AWG 150 V UW-1 - LL50890 CSA AWM I A/B 300 VFT1
11/99 (918 X)


---

### Post by tseliot on 2005-11-27
[QUOTE=Freddd]The writings of the cable says:[/QUOTE]

I have no clue. Buy another cable as well, it can always come in handy.

---

### Post by alvinblank on 2005-11-27
I'm kinda having the same problem, just not as long. hdpram reports both my hd are dma on. My cable is 80pin but both jumper on the hd are set to cable-select (not sure if it does any damage). Any idea? Boot-splash shows for awhile with Loading Modules, than back to console saying Loading please wait. This take about 10 to 20 seconds.

EDIT: To add, it's a WD hd. I've a MAXTOR slave but I can't touch that for Ubuntu. Stuck with this WD.

---

### Post by tseliot on 2005-11-27
[QUOTE=alvinblank]I'm kinda having the same problem, just not as long. hdpram reports both my hd are dma on. My cable is 80pin but both jumper on the hd are set to cable-select (not sure if it does any damage). Any idea? Boot-splash shows for awhile with Loading Modules, than back to console saying Loading please wait. This take about 10 to 20 seconds.

EDIT: To add, it's a WD hd. I've a MAXTOR slave but I can't touch that for Ubuntu. Stuck with this WD.[/QUOTE]
I think it's normal

---

### Post by alvinblank on 2005-11-27
Is there a progress bar for the boot? I remember when I was with fedora, their boot process is damn sweet. Would like to find a way to do that.

---

### Post by KompresZor on 2005-11-28
Ultra DMA ( 80 conductor 40 pin ) Blue/Gray/Black connectors

motherboard--------slave---------master
blue----------------gray----------black

This is the way cable select is designed to work on 80-conductor 40 pin cables. I never use cable-select because most 40 conductor 40 pin cables wont support it and setting the jumpers was just eaiser then buying a special cable ;)  I use this scheme even if I set the drives jumpers to master/slave, it makes for less human errors. 

The OS should be installed on the drive that is the Master on the Primary IDE Channel.

If you only have a single drive, connect it to the **end** of the cable and **not the middle**. The left over, unconnected cable will cause signaling problems.

Here is a good reference that I use when I'm in doubt [Reference Guide]("http://www.storagereview.com/guide2000/ref/hdd/if/ide/conf.html")

---

### Post by ed_d on 2005-11-28
Get yourself a SCSI drive and controller. That way not using the system bus, but rather the SCSI card itself. Mine are U160s and work very well. I have never liked IDE drives all that much. Guess dont like the fact that only 2 drives per bus myself. Plus, I do a lot of servers and SCSI is the main disk of choice.

---

### Post by Freddd on 2005-11-28
My hard disc isn't working at all now! I'm trying to reinstall ubuntu but it hangs at 100 % every time when I'm at the part where it partionates the disc.

Any idea? Is it possible to only format the disc and begin from scratch?

---

### Post by tseliot on 2005-11-28
[QUOTE=Freddd]My hard disc isn't working at all now! I'm trying to reinstall ubuntu but it hangs at 100 % every time when I'm at the part where it partionates the disc.

Any idea? Is it possible to only format the disc and begin from scratch?[/QUOTE]
What did you do? Did you change the cable?
Please list every single change.

---

### Post by Freddd on 2005-11-28
I didn't do anything except repairing the pin that was bended. Linux finds my hard disc but it hangs on the same place everytime.

I can see two options:
1. It's my fault
2. The hard disc was bad from the beginning and now it finally crashed.

I will try to install again. But isn't there no way to format the hard disc? Maybe it's the data the causes problem when I try to reinstall?

---

### Post by tseliot on 2005-11-28
[QUOTE=Freddd]I didn't do anything except repairing the pin that was bended. Linux finds my hard disc but it hangs on the same place everytime.

I can see two options:
1. It's my fault
2. The hard disc was bad from the beginning and now it finally crashed.

I will try to install again. But isn't there no way to format the hard disc? Maybe it's the data the causes problem when I try to reinstall?[/QUOTE]
I guess the 2nd option is the most likely.

---

### Post by Freddd on 2005-11-28
Good, I will return tomorrow hopefully. I let you now about it when it is installed. Thanks for all the time you have spent helping me :)

---

