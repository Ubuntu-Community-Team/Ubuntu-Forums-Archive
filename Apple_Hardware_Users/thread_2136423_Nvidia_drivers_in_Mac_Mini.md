---
title: "Nvidia drivers in Mac Mini"
date: 2013-04-17
forum: Apple Hardware Users
---

### Post by Laski on 2013-04-17
Hi! I've recently installed Ubuntu in a Mac Mini that I recieved in my work. The problem is that, when I install NVidia propietary drivers, blacklist nouveau and reboot, the grub and the logo are shown but then the monitor turns black and finds no input. As I can tell from the logs, the drivers are working correctly (no errors). I've tried vaaarious versions of them, always with the same result.

I read somewhere that it could be a problem with BIOS/EFI, but the output:

$  [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"  
EFI boot on HDD

shows that I'm booting with EFI (what, as far a I've read, is the correct approach). Should I try booting with Legacy BIOS?
Another (maybe) useful note is that my monitor is connected to the Thunderbolt port with a Thundebolt-HDMI cable, because I haven't got any HDMI-HDMI cable. With noveau drivers the monitor just works (I'm in the Mac right now writing this).

Here's the output of 
$ lspci | grep VGA
05:00.0 VGA compatible controller: NVIDIA Corporation MCP89 [GeForce 320M] (rev a2)

and the end of the xorg log when I try to boot with NVidia drivers (and left for 10 minutes with the monitor trying to find an input):

$ tail Xorg.log 
[    22.274]     ABI class: X.Org ANSI C Emulation, version 0.4
[    22.274] (II) Loading sub module "ramdac"
[    22.274] (II) LoadModule: "ramdac"
[    22.274] (II) Module "ramdac" already built-in
[    22.274] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    22.274] (==) NVIDIA(0): RGB weight 888
[    22.274] (==) NVIDIA(0): Default visual is TrueColor
[    22.274] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    22.274] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[    22.274] (**) NVIDIA(0): Enabling 2D acceleration

Thank you very much!

---

### Post by Julien Dutant on 2014-03-01
I have a similar problem on a MacBook Air 3,2 (nvidia G320M). The solution is clearly to run in BIOS mode: the nvidia drivers don't work with EFI. I managed to switch to BIOS mode on my laptop and after that the drivers (nvidia-319) worked flawlessly. NB, after installing the drivers, you need to run sudo nvidia-xconfig before you restart.

Setting up Ubuntu in BIOS mode can be tricky. The simplest is (apparently) to install it from a CD. (This may require pressing "alt option" at the white screen on boot and choosing the "Windows CD" option, I've read). In my case I don't have a CD drive for the laptop. I didn't find a simple solution online to switch to BIOS mode. I managed by doing an install with a bios_grub partition, running the Live usb stick again, and using Boot repair. I'm trying to redo it now but getting into trouble. Once solved I'll post.

---

