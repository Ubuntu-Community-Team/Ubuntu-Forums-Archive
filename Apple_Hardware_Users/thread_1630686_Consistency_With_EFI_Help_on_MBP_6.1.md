---
title: "Consistency With EFI Help on MBP 6.1"
date: 2010-11-25
forum: Apple Hardware Users
---

### Post by eusanpe on 2010-11-25
Hello All,

I just got a 17" MBP (6.1) with two OCZ Vertex2 480GB drives. I want to do an install without OSX. I want to use EFI and grub2 because I have two video cards. I don't want to use ReFit nor am I going to dual boot. I have OSX installed on an external drive. I have things working with legacy bios compatibility with boot as a Raid1 and root as Raid0, but I can't take advantage of the Intel video card.

I have been browsing the forums and the internet and I can't find any consistency with how to set this up. Some say create a Fat32 partition using efi/boot, others say /efi/grub and another says create a HFS+ partition under efi/grub and bless it. 

Is there a howto on how to set this up that is the proper way? Maybe all of these ways are proper but I can't get them to work no matter what I try.

All I am looking for is:

1. Proper way to partition boot..fat32, ext2, hfs+ or anything else.
2. The location of boot.../efi/boot, /efi/grub, /efi/boot/grub,   
   /boot/grub, /EFI/BOOT
3. Proper file name...grub.efi, bootx64.efi or BOOTX64.EFI
4. Getting Grub-1.99 to grub-install properly wihout embedding errors.

I think I can get the grub.cfg according to other user settings.

Any help would be appreciated.


Tony

---

### Post by metatechbe on 2010-11-26
> **eusanpe said:**
> 
Is there a howto on how to set this up that is the proper way? Maybe all of these ways are proper but I can't get them to work no matter what I try.

Hi eusanpe,
Did you already see these instructions  ?
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)
What errors do you have ?
Regards,
metatech

---

### Post by eusanpe on 2010-11-26
Thank you for replying. I followed the directions partly.
> Here is my setup:
raid1 - /dev/md1 (hfsplus)   metadata=0.90   /dev/sda1 /dev/sda2
raid0 - /dev/md2 (ext4)      metadate=0.90   /dev/sda2 /dev/sdb2

I performed the following steps from Testing on Macbook Pro
I am using Grub-1.99 from bzr

./configure --with-platform=efi --target=x86_64 --program-prefix=""
make
make install

cd grub-core
../grub-mkimage -O x86_64-efi -d . -o grub.efi -p "" part_gpt hfsplus fat ext2 normal chain boot configfile linux multiboot raid mdraid09
cp grub.efi *.mod *.lst /boot/grub

grub-mkdevicemap for my devices.
grub-install /dev/md1

(no errors with grub-install)

mdadm --detail --scan >>/etc/mdadm.conf

Booted OSX from Install DVD
----------------------------
The two hfsplus partitions were automatically mounted in diskutil

bless --folder=/Volumes/boot --file=/Volumes/boot/grub/grub.efi --setBoot
bless --folder=/Volumes/boot\ 1 --file=/Volumes/boot\ 1/grub/grub.efi --setBoot

grub-mkdevicemap for my devices.
grub-install /dev/md1

This produced no errors.

dd if=/dev/mem of=/boot/vbios.bin bs=65536 skip=12 count=1
dd if=/dev/mem of=/boot/int10.bin bs=4 skip=16 count=1


Contents of grub.cfg. This is from the edit command from the grub menu.
-----------------------------------------------------------------------
setparams "Ubuntu (with bios dump)"
insmod efi_gop
search --set -f /vmlinuz
loadbios /vbios.bin /int10.bin
set root (hd0,1)
linux /vmlinuz root=/dev/md2 video=efifb


setparams "Ubuntu (with bios dump and fix video)"
insmod efi_gop
insmod raid
insmod mdraid09
search --set -f /vmlinuz
fix_video
loadbios /vbios.bin /int10.bin
set root (hd0,1)
linux /vmlinuz root=/dev/md2 video=efifb


setparams "Ubuntu fakebios)"
insmod efi_gop
insmod raid
insmod mdraid09
search --set -f /vmlinuz
fakebios
set root (hd0,1)
linux /vmlinuz root=/dev/md2 video=efifb

----------------------------------------------------------
When I select the first entry, I get the 'Booting a command list' and it just sits there. If I comment out the loadbios command, the 'Booting a command list' comes up and then the screen goes blank.

I apended the parameters of base, stride, width and height to the video=efifb line but to no avail. I tried taking out loadbios, video=efifb and adding noefi but nothing happens.

I am using kernel 2.6.36 and I have fbcon and efifb in the kernel


fstab    /dev/md1   /boot     hfsplus   defaults   0 2
         /dev/md2   /         ext4      noatime    1 2



If you need any other info, please let me know. I am going to try to set this up without the raid just to see. I use this exact setup without grub-efi with bios-compatibility mode and it works great.

Thanks,
Tony

---

### Post by metatechbe on 2010-11-27
> **eusanpe said:**
> Thank you for replying. I followed the directions partly.


If you need any other info, please let me know. I am going to try to set this up without the raid just to see. I use this exact setup without grub-efi with bios-compatibility mode and it works great.

Thanks,
Tony

Hello,

Have you tried without the base, stride, width and height parameters ?
Adding them seems to behave badly on my machine, and anyway they should not be necessary with grub 1.99(beta).

metatech

---

### Post by metatechbe on 2010-11-27
Hi Tony

Sidolin managed to manage to EFI boot a MacBookPro6,2, but he needed to apply the following patch : 
[https://patchwork.kernel.org/patch/119823/](https://patchwork.kernel.org/patch/119823/)
see [http://ubuntuforums.org/showpost.php?p=9822192&postcount=1140](http://ubuntuforums.org/showpost.php?p=9822192&postcount=1140)

He also told me that he applied the following patches, but he think they were not really necessary :
0001-i915-lvds-dual-channel-workaround-driver-doesn't-detect-the-display-needs-dual-channel-mode.patch
0001-intel-display-ddc-lock.patch
0001-nouveau-interrupt-conflict-fix.patch
0001-nouveau-restore-registers-needed-to-work-with-efi.patch
0001-switcheroo-lock-ddc.patch
[http://andreas.meetr.de/gmux/](http://andreas.meetr.de/gmux/)

Good luck,
Regards,

metatech

---

### Post by eusanpe on 2010-11-29
metatech...thank you for your help. I was finally able to get it to boot up. I had to use the noefi parameter to use it. I will look more into the noefi patch. Now I will have to figure out xorg.conf.


Thank you again,
Tony

---

### Post by devoda on 2010-12-02
Eusanpe, Did you figure out your xorg.conf? If so, would you send me a copy of it through private message. I am also in EFI mode on a mbp 6,2 but can only boot framebuffer and am having trouble selecting integrated card. How far have you gotten. Thanks and good luck.

---

### Post by metatechbe on 2010-12-03
> **devoda said:**
> Eusanpe, Did you figure out your xorg.conf? If so, would you send me a copy of it through private message. I am also in EFI mode on a mbp 6,2 but can only boot framebuffer and am having trouble selecting integrated card. How far have you gotten. Thanks and good luck.

Please share your config on the forum, I am sure it will be very helpful for future EFI booters.
Thanks.

metatech

---

### Post by eusanpe on 2010-12-21
I never did figure out my xorg.conf. While testing, my system kept crashing. I took my laptop to the apple store and they replaced the logic board. Not even 30 days old..dangit. I just got back from vacation so I will mess with it. Once I figure out how to get things working, I will post my configs.


Thanks
Tony

---

### Post by paulcz on 2011-02-10
i currently trying to get that stuff working on a macbook pro 6,2.

i have gotten past booting, which drops me to CLI.

adding

BusID   "PCI:1:0:0"

to the Device Section of the xorg.conf "starts" X but gives me blank screen.

starting an ssh session on a different machine and looking into the log files might give me some more info ... which will be my next step i guess.

EDIT:
after connecting via ssh: i was wrong. adding the above line does not start X. X fails for the same reason as before ... it just blanks the screen aswell :p.

EDIT:
ok ... blacklisting i915 and intel_agp and using

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fbdev"
EndSection

as xorg.conf gives me a "working" X, but no 3d accel ... i need nvidea driver working.

EDIT:
last one for today.
i ended up patching my kernel using:
[https://patchwork.kernel.org/patch/119823/](https://patchwork.kernel.org/patch/119823/)

now can boot with efi without using the kernel parameter noefi. so my grub entry looks like that:
 > 
  insmod efi_gop
  insmod part_gpt
  insmod ext2
  set root='(hd1,gpt3)'
  loadbios /boot/vbios.bin /boot/int10.bin
  linux /vmlinuz root=/dev/sda3 video=efifb nopat
  initrd /initrd.img


but i still can't get the properitary nvidea driver working.
after installing the latest from the nvidea website i get something like no device found.
after adding the above:

> 
BusID   "PCI:1:0:0"


i get the following logfile:
> 
[   423.395] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   423.395] X Protocol Version 11, Revision 0
[   423.395] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[   423.395] Current Operating System: Linux protos 2.6.35.10mbpro62-custom #1 SMP Thu Feb 10 21:05:50 CET 2011 x86_64
[   423.395] Kernel command line: BOOT_IMAGE=/vmlinuz root=/dev/sda3 video=efifb nopat
[   423.395] Build Date: 09 January 2011  12:14:27PM
[   423.395] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   423.395] Current version of pixman: 0.18.4
[   423.395] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[   423.395] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   423.395] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb 10 23:19:47 2011
[   423.396] (==) Using config file: "/etc/X11/xorg.conf"
[   423.396] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   423.396] (==) ServerLayout "Layout0"
[   423.396] (**) |-->Screen "Screen0" (0)
[   423.396] (**) |   |-->Monitor "Monitor0"
[   423.396] (**) |   |-->Device "Device0"
[   423.396] (**) |-->Input Device "Keyboard0"
[   423.396] (**) |-->Input Device "Mouse0"
[   423.396] (==) Automatically adding devices
[   423.396] (==) Automatically enabling devices
[   423.396] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   423.396] 	Entry deleted from font path.
[   423.396] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   423.396] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   423.396] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   423.396] (WW) Disabling Keyboard0
[   423.396] (WW) Disabling Mouse0
[   423.396] (II) Loader magic: 0x7d17a0
[   423.396] (II) Module ABI versions:
[   423.396] 	X.Org ANSI C Emulation: 0.4
[   423.396] 	X.Org Video Driver: 8.0
[   423.396] 	X.Org XInput driver : 11.0
[   423.396] 	X.Org Server Extension : 4.0
[   423.398] (--) PCI:*(0:0:2:0) 8086:0046:0000:0000 rev 24, Mem @ 0xc1400000/4194304, 0xb0000000/268435456, I/O @ 0x00003130/8
[   423.398] (--) PCI: (0:1:0:0) 10de:0a29:106b:00c7 rev 162, Mem @ 0xc0000000/16777216, 0x90000000/268435456, 0xa0000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/524288
[   423.398] (II) Open ACPI successful (/var/run/acpid.socket)
[   423.398] (II) LoadModule: "extmod"
[   423.399] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   423.399] (II) Module extmod: vendor="X.Org Foundation"
[   423.399] 	compiled for 1.9.0, module version = 1.0.0
[   423.399] 	Module class: X.Org Server Extension
[   423.399] 	ABI class: X.Org Server Extension, version 4.0
[   423.399] (II) Loading extension MIT-SCREEN-SAVER
[   423.399] (II) Loading extension XFree86-VidModeExtension
[   423.399] (II) Loading extension XFree86-DGA
[   423.399] (II) Loading extension DPMS
[   423.399] (II) Loading extension XVideo
[   423.399] (II) Loading extension XVideo-MotionCompensation
[   423.399] (II) Loading extension X-Resource
[   423.399] (II) LoadModule: "dbe"
[   423.400] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   423.400] (II) Module dbe: vendor="X.Org Foundation"
[   423.400] 	compiled for 1.9.0, module version = 1.0.0
[   423.400] 	Module class: X.Org Server Extension
[   423.400] 	ABI class: X.Org Server Extension, version 4.0
[   423.400] (II) Loading extension DOUBLE-BUFFER
[   423.400] (II) LoadModule: "glx"
[   423.400] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   423.407] (II) Module glx: vendor="NVIDIA Corporation"
[   423.407] 	compiled for 4.0.2, module version = 1.0.0
[   423.407] 	Module class: X.Org Server Extension
[   423.407] (II) NVIDIA GLX Module  260.19.36  Tue Jan 18 17:12:12 PST 2011
[   423.407] (II) Loading extension GLX
[   423.407] (II) LoadModule: "record"
[   423.407] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   423.407] (II) Module record: vendor="X.Org Foundation"
[   423.407] 	compiled for 1.9.0, module version = 1.13.0
[   423.407] 	Module class: X.Org Server Extension
[   423.407] 	ABI class: X.Org Server Extension, version 4.0
[   423.407] (II) Loading extension RECORD
[   423.407] (II) LoadModule: "dri"
[   423.408] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   423.408] (II) Module dri: vendor="X.Org Foundation"
[   423.408] 	compiled for 1.9.0, module version = 1.0.0
[   423.408] 	ABI class: X.Org Server Extension, version 4.0
[   423.408] (II) Loading extension XFree86-DRI
[   423.408] (II) LoadModule: "dri2"
[   423.408] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   423.408] (II) Module dri2: vendor="X.Org Foundation"
[   423.408] 	compiled for 1.9.0, module version = 1.2.0
[   423.408] 	ABI class: X.Org Server Extension, version 4.0
[   423.408] (II) Loading extension DRI2
[   423.408] (II) LoadModule: "nvidia"
[   423.408] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[   423.408] (II) Module nvidia: vendor="NVIDIA Corporation"
[   423.408] 	compiled for 4.0.2, module version = 1.0.0
[   423.408] 	Module class: X.Org Video Driver
[   423.408] (II) NVIDIA dlloader X Driver  260.19.36  Tue Jan 18 16:57:32 PST 2011
[   423.408] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   423.408] (--) using VT number 8

[   423.592] (II) Loading sub module "fb"
[   423.592] (II) LoadModule: "fb"
[   423.592] (II) Loading /usr/lib/xorg/modules/libfb.so
[   423.592] (II) Module fb: vendor="X.Org Foundation"
[   423.592] 	compiled for 1.9.0, module version = 1.0.0
[   423.592] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   423.592] (II) Loading sub module "wfb"
[   423.592] (II) LoadModule: "wfb"
[   423.592] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   423.592] (II) Module wfb: vendor="X.Org Foundation"
[   423.592] 	compiled for 1.9.0, module version = 1.0.0
[   423.592] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   423.592] (II) Loading sub module "ramdac"
[   423.592] (II) LoadModule: "ramdac"
[   423.592] (II) Module "ramdac" already built-in
[   423.593] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   423.593] (==) NVIDIA(0): RGB weight 888
[   423.593] (==) NVIDIA(0): Default visual is TrueColor
[   423.593] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   423.593] (**) NVIDIA(0): Enabling RENDER acceleration
[   423.593] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[   423.593] (II) NVIDIA(0):     enabled.
[   423.770] (EE) NVIDIA(0): Failed to initialize the display subsystem for the NVIDIA
[   423.770] (EE) NVIDIA(0):     graphics device!
[   423.770] (EE) NVIDIA(0): Failed to determine chip display capabilities
[   423.771] (EE) NVIDIA(GPU-0): Failed to get supported display device(s)
[   423.771] (EE) NVIDIA(0): Failed to initialize dac HAL
[   423.776] (II) UnloadModule: "nvidia"
[   423.776] (II) UnloadModule: "wfb"
[   423.776] (II) UnloadModule: "fb"
[   423.776] (EE) Screen(s) found, but none have a usable configuration.
[   423.776] 
Fatal server error:
[   423.776] no screens found
[   423.776] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   423.776] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   423.776] 
[   424.184]  ddxSigGiveUp: Closing log



any thoughts?

---

