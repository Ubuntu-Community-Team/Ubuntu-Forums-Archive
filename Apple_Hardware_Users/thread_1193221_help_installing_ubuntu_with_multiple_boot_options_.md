---
title: "help installing ubuntu with multiple boot options on a firewire 800 drive (macbookpro"
date: 2009-06-21
forum: Apple Hardware Users
---

### Post by bjaz on 2009-06-21
hello all
as a follow up to this thread 
[http://ubuntuforums.org/showthread.p...21#post7484021]("http://ubuntuforums.org/showthread.php?p=7484021#post7484021")

i'm stuck trying to install ubuntu studio on a firewire 800 drive.
the drive contains two other bootable mac OS's ( 10.4 and 10.5, dedicated to audio and video tasks), and a large ntfs storage space for the two oss's
the drive is a recent firewire 800, 1To, bootable. the machine, a macbook pro, has had no issues with firewire drive booting

the drive, identified as sdb, lets me install ubuntu studio on a dedicated 30 Gig partition in ext4
the partition is bootable, mounted as root / mount point
sbd6

there is a 10gig SWAP partition, use as swap, which is labelled sdb2

installing goes well. i choose manual install, erase and format the dedicated partition to ext.4, designate a / root mount point, bootable 
yet i've had issues with the grub install. i tried to specify the partition on which to install and got a fatal error. it finally worked, i think, with /dev/sdb as a location

i got an "install complete" message, and was asked to restart. yet upon restart it boots directly onto the firewire drive's mac os.

now when i start the machine and press the alt key, usual alternate boot option, i get a choice between 
mac os on my internal hard drive, 
windows xp boot camp on my internal hard drive,
 the two mac os's on the firewire drive,
 and a **new partition on the firewire drive recognised as "windows"**, which i believe is due to the grub install

unfortunately, choosing this "windows" actually boots onto the internal drive's windows xp, instead of the sdb6 ubuntu studio install...

i can't tell if the ubuntu studio os was actually installed or not, as i've never been able to boot into it.

i've tried redoing the install a few times, but to no avail

now i'm really stuck, reading up, or trying to, is becoming confusing

any ideas on how to to check that the system is installed, boot into it or make it bootable would be great

my only concern is to protect the two (work specialized environments) mac os's on the firewire partition as well as a 600 gig ntfs+ storage space which contains work related data

i could do without one of the os's I guess, could clone it on another drive but i really need the storage space and one specialised os on this firewire drive, and would love to dive into to ubuntu studio as well


thanks greatly

ben

---

### Post by bjaz on 2009-06-22
is this actually possible ?

i'm really not finding my way out of this.

thanks

ben

---

### Post by bjaz on 2009-06-22
after doing so reading, i found out about rEFIT, and installed that.
i then redid a clean erase reformat (in ext3) mount a / of the ubuntu partition, sdb6, the grub installed on dev/sdb, and sdb2 being my swap,
now when i boot into the firewire drive's mac os, on which i installed rEFIT, i can choose between the 2 different mac os's, and 2 (don't know why there's two) linux os's
entitled linux from HD and linux from EFI

yet neither of them can be booted into. i get 
---------
starting legacy loader using load options "USB"
Error not found returned from legacy loader
the firmware refused to boot from the selected volume. note that external hard drives are not well-supported by Apple's firmware for legacy OS booting
----------

thing is this firewire 800 drive works fine for booting the two mac os's which are on it.
is there anyway to fix this so that i can finally boot into ubuntu ?

thanks

ben

---

### Post by vonlaken on 2009-06-22
use rEFIt to start grub2 (from here [http://ubuntuforums.org/showpost.php?p=6966036&postcount=523](http://ubuntuforums.org/showpost.php?p=6966036&postcount=523)), and set boot parameters in grub2..... forget classic grub

place grub2 next to the rEFIt file and make a grub.cfg file with

menuentry "XXXXX"
root (X,6)   <----- probably 1,6
video_fix
linux /vmlinuz root=/sdb6 video=efifb <------ And other params as needed
initrd /initrz.gz
boot

---

### Post by pxwpxw on 2009-06-23
I have posted a current version of grub64.efi plus grub.cfg for external booting in a small package at post #772 on the grub efi thread.

---

### Post by bjaz on 2009-06-23
oh this great.
i would just need a little help to do things right, since so far what i've tried has given me the EfiBoot option, but i'm not sure how to use it properly.

i downloaded  grub64.efi plus grub.cfg  and placed this inside the rEfit folder at the root of the mac partition

now when i boot, i have the grub64 rEFIboot option.

is this ok or did i miss a step ?

i tried to edit the cfg, using text edit, adding the following which brings me a new entry in the refiboot 

menuentry Ubuntu Studio
root (1,6)
video_fix
linux /vmlinuz root=/sdb6 video=efifb
initrd /initrz.gz
boot     

-----

this got a "no such partition", so i guess there's an issue somewhere in it's localisation.
i'm doing a clean re-install without the GRUB as i type. the computer i'm typing on runs xubuntu, and i used it to check that the sdb6 ext# partition was ok, it mounted with no problem, and the install looked complete. 

the partition manager gives me the partition's name as SCSI5 0,0,0 sdb
the partition is in ext3, #6

i'm wondering if i'm geting the options right when i do the manual partitioning upon install. i choose use as root, mount to /, bootable flag on when i install

---

### Post by bjaz on 2009-06-23
tried adding lines to cfg file.

i'm not quite sure how what to add precisely to the cfg file in order to boot on sdb6

---

### Post by pxwpxw on 2009-06-23
Hang on, I am answering now

---

### Post by bjaz on 2009-06-23
> **pxwpxw said:**
> Hang on, I am answering now
  

thanks.  the current grub.cfg (grub2) i just tried is the following (added the external ubuntu studio entry).
the mac i'm using is a macbookpro 2.2GHz intel core 2 duo-

-------------

# grub.cfg for external drive pxw 20090623

timeout=20
default=0

set F1=ctrl-x
set F2=ctrl-c
set color_normal=yellow/blue

menuentry "OSX" {
    search --set /usr/standalone/i386/boot.efi
    chainloader /usr/standalone/i386/boot.efi
}
menuentry "internal OSX on sda2" {
    root=hd1,2
    chainloader /usr/standalone/i386/boot.efi
}
menuentry "external sdb2 fbdev root console" {
    fakebios
    root=hd0,2
    linux /vmlinuz root=/dev/sdb2 video=efifb noefi single
    initrd /initrd.img
}
menuentry "external Ubuntu Studio" {
    root=hd0,6
    linux /vmlinuz root=/dev/sdb6 video=efifb 
    initrd /initrz.gz
        boot
}
menuentry "external sdb2 fbdev login" {
    fakebios
    root=hd0,2
    linux /vmlinuz root=/dev/sdb2 video=efifb noefi
    initrd /initrd.img
}
menuentry "internal sda3 fbdev root console" {
    fakebios
    root=hd1,3
    linux /vmlinuz root=/dev/sda3 video=efifb noefi single
    initrd /initrd.img
}
menuentry "internal sda3 fbdev login" {
    fakebios
    root=hd1,3
    linux /vmlinuz root=/dev/sda3 video=efifb noefi
    initrd /initrd.img
}
# ati fglrx on ubuntu810 for 3d accel (imac81)
menuentry "external fglrx sdb2" {
    search --set /boot/vbios.bin
    loadbios /boot/vbios.bin /boot/int10.bin
    root=hd0,2
    linux /vmlinuz root=/dev/sdb2 video=vesafb
    initrd /initrd.img
}
menuentry "internal CD" {
   appleloader CD
}
menuentry "internal MBR1" {
   appleloader HD
}
menuentry "REBOOT" {
    reboot
}


--------------------

---

### Post by pxwpxw on 2009-06-23
> **bjaz said:**
> thanks.  the current grub.cfg (grub2) i just tried is the following (added the external ubuntu studio entry).
the mac i'm using is a macbookpro 2.2GHz intel core 2 duo-

-------------

# grub.cfg for external drive pxw 20090623

timeout=20
default=0

set F1=ctrl-x
set F2=ctrl-c
set color_normal=yellow/blue

menuentry "OSX" {
    search --set /usr/standalone/i386/boot.efi
    chainloader /usr/standalone/i386/boot.efi
}
menuentry "internal OSX on sda2" {
    root=hd1,2
    chainloader /usr/standalone/i386/boot.efi
}
menuentry "external sdb2 fbdev root console" {
    fakebios
    root=hd0,2
    linux /vmlinuz root=/dev/sdb2 video=efifb noefi single
    initrd /initrd.img
}
menuentry "external Ubuntu Studio" {
    root=hd0,6
    linux /vmlinuz root=/dev/sdb6 video=efifb 
    initrd [COLOR="Red"]/initrz.gz[/COLOR]
        boot
}
--------------------
Yes thats better, but you have typos.

The boot menu you see is the grub.efi boot menu, rEFIt just finds and starts grub.efi, you should see the grub64.efi icon in the rEFIt screen.
It is possible to boot without rEFIt, but more difficult to set up.

Your external drive is hd0 according to grub.efi, but the linux kernel still sees it as /dev/sdb. So it will be root=hd0,6 but linux /vmlinuz root=/dev/sdb6.

You don't need 'boot' in the menuentry.

video_fix does not exist, it is fix_video, but it only works for intel video chips.

Also see the references in #comments at the tail end of the grub.cfg.

grub2 command language is not like grub1.

menuentry "external sdb6 fbdev root console" {
	fakebios
	root=hd0,6
	linux /vmlinuz root=/dev/sdb6 video=efifb noefi single
	initrd /initrd.img
}

That should boot to a root console.

---

### Post by bjaz on 2009-06-23
thank you so much for your time and help !

it worked- yet i'm getting graphical problems, leading to a disabled X server. 
i wonder what this could be due to.

i end up in discovery mode. trying with an auto repair graphic problems

- getting a"failed to start the X server."
fatal server error
no screens found



odd... is this a common issue ?
this is on  a macbook pro.

i tried 
sudo dmidecode -s system-product-name
and got 

MacBookPro 3,1

wonder if this is a santa rosa, from what i7m reading there are known issues
ben

---

### Post by pxwpxw on 2009-06-23
> **bjaz said:**
> thank you so much for your time and help !

it worked- yet i'm getting graphical problems, leading to a disabled X server. 
i wonder what this could be due to.

i end up in discovery mode. trying with an auto repair graphic problems

- getting a"failed to start the X server."
fatal server error
no screens found



odd... is this a common issue ?
this is on  a macbook pro.

i tried 
sudo dmidecode -s system-product-name
and got 

MacBookPro 3,1

wonder if this is a santa rosa, from what i7m reading there are known issues
ben

Thats ok, normal, you have to boot into a root console as I said above to set it up. Please see the grub2 efi thread, post #776 details how to set it up to use the xorg Driver "fbdev" which will get you to a desktop, just no 3d accelerated graphics but otherwise nice. 

What is your graphics chip -
```

$ sudo lspci -nn | grep VGA

```

Intel or Radeon can do 3d accel (sometimes).

I think you may have intel graphics? That would be better, but try the fbdev setup to get a desktop and make it easier to go from there.

---

### Post by bjaz on 2009-06-23
the graphic  chipset is GeForce8600 GT
NVDVIA

i'm trying to do what is described in post 776 of the efigrub thread.

the option is already UseFBDev "true"

I edit the x11.conf

replacing with

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fbdev"
EndSection

---

### Post by pxwpxw on 2009-06-23
> **bjaz said:**
> don't know about the intel chip, couldn't try out the command line because i can't seem to be able to get the pipe sign on this french keyboard.

i'm trying to do what is described in post 776 of the efigrub thread.

the option is already UseFBDev "true"

No, thats not it, make a backup copy as explained in #776 and replace the xorg.conf using just the single Section "Device" exactly as shown in 776.

```

Section "Device"
	Identifier "Configured Video Device"
	Driver "fbdev"
EndSection

```

---

### Post by bjaz on 2009-06-23
I just did this.
and also copied the xconf log, which follows.

unplugging the drive (connected it to the xubuntu running machine to do the changes) and rebooting on it now

----

my xconf now reads :



Section "Device"
        Identifier "Configured Video Device"
        Driver "fbdev"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


-----

the log

--------

    GeForce 7900 GS, GeForce Go 7900 GS, GeForce Go 7900 GTX,
    Quadro FX 2500M, Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500,
    Quadro FX 1500, Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE,
    GeForce 6100, GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX,
    GeForce 8800 GTS, GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600,
    GeForce 8600 GTS, GeForce 8600 GT, GeForce 8600 GT, GeForce 8600 GS,
    GeForce 8400 GS, GeForce 9500M GS, GeForce 8600M GT,
    GeForce 9650M GS, GeForce 8700M GT, Quadro FX 370, Quadro NVS 320M,
    Quadro FX 570M, Quadro FX 1600M, Quadro FX 570, Quadro FX 1700,
    GeForce 8400 SE, GeForce 8500 GT, GeForce 8400 GS, GeForce 8300 GS,
    GeForce 8400 GS, GeForce 8600M GS, GeForce 8400M GT,
    GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
    Quadro NVS 135M, GeForce 9400 GT, Quadro FX 360M, GeForce 9300M G,
    Quadro NVS 290, GeForce GTX 280, GeForce GTX 260,
    GeForce 8800 GTS 512, GeForce 8800 GT, GeForce 9800 GX2,
    GeForce 8800 GS, GeForce 8800M GTS, GeForce 8800M GTX,
    GeForce 8800 GS, GeForce 9600 GSO, GeForce 8800 GT, GeForce 9800 GTX,
    GeForce 9800 GTK+, GeForce 9800 GT, GeForce GTS 250, Quadro FX 3700,
    Quadro FX 3600M, GeForce 9600 GT, GeForce 9600 GS, GeForce 9800M GTS,
    GeForce 9700M GTS, GeForce 9800M GTS, GeForce 9500 GT,
    GeForce 9600M GT, GeForce 9600M GS, GeForce 9600M GT,
    GeForce 9500M G, GeForce 9300 GS, GeForce 8400 GS, GeForce 9300M GS,
    GeForce 9200M GS, GeForce 9300M GS, Quadro NVS 150M, Quadro NVS 160M
(II) Primary Device is: PCI 01@00:00:0
(--) NV: Found NVIDIA GeForce 8600M GT at 01@00:00:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) NV(0): Initializing int10
(EE) NV(0): V_BIOS address 0x0 out of range
(WW) NV(0): Failed to initialize the int10 module; the console will not be restored.
(II) NV(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(==) NV(0): Using hardware cursor
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): MMIO registers mapped at 0x7fd427d7e000
(--) NV(0): Total video RAM: 128.0 MB
(--) NV(0):       BAR1 size: 256.0 MB
(--) NV(0):   Mapped memory: 127.0 MB
(II) NV(0): Linear framebuffer mapped at 0x7fd41fe7e000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(EE) NV(0): Couldn't find the DDC routing table.  Mode setting will probably fail!
(II) UnloadModule: "nv"
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

### Post by bjaz on 2009-06-23
success !

finally reached a desktop, i'm really glad (i'd been trying for weeks).

 thank you so much for your patience and help.
is there anyway to simplify the booting process, launching it through an icon like the other os's ?
otherwise it's fine like this, it's just that i might not be the only person using this machine in the future

thanks again

ben

---

### Post by pxwpxw on 2009-06-23
> **bjaz said:**
> success !

finally reached a desktop, i'm really glad (i'd been trying for weeks).

 thank you so much for your patience and help.
is there anyway to simplify the booting process, launching it through an icon like the other os's ?
otherwise it's fine like this, it's just that i might not be the only person using this machine in the future

thanks again

ben

Yes we can make it easier to boot, by a few changes, but I will have to leave it there just now, and you can sort out what you have and what you want, then let me know here.

Note that the Xorg.0.log shows that it was loading the 'nv' driver before you fixed it, and we have not been able to get that working with grub.efi so far, so you will be stuck with 'fbdev' for now. It is possible to reinstall for a boot from grub1 and a /boot partition on the internal drive if you want to have the nvida 3d accel drivers, but thats another story.

---

### Post by bjaz on 2009-06-23
i understand, thanks.
as of now, strangely enough i had to redo the changes in the xorg.cong to boot again.
i'm trying to download the updates via an ethernet cable connection, but it's not working.

b

---

### Post by bjaz on 2009-06-24
internet is fixed.
yet this is strange, i'm getting booting problems again.
when i go into the rEFIit grub 2 and choose the sdb6 partition, i get "error, you need to load the kernel first"
this seems to be fixed by unplugging the drive and rebooting, but not always.

i checked the grub.conf and nothing has changed apparently. 

odd

---

### Post by Richardcavell on 2009-06-24
Hey,

Could you guys who are good with the EFI/booting Linux from external drives thing please post some foolproof instructions for getting it to work?  So far, the instructions posted on this forum are obscure and don't cover general cases.

Richard

---

