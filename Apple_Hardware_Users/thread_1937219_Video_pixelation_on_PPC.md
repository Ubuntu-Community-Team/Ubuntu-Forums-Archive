---
title: "Video pixelation on PPC"
date: 2012-03-07
forum: Apple Hardware Users
---

### Post by Improntant on 2012-03-07
I recently installed Ubuntu 10.04 on my PPC G4 eMac. It's way faster than Mac OS X, but video playback is pixelated. I think there is a fix for this in [PowerPCFAQ]("https://wiki.ubuntu.com/PowerPCFAQ#Are_there_any_radeon_tweaks_I_can_do.3F"), but I'm not sure if I'm doing it right. > With 10.04 and 10.10 I turn off KMS (Kernel Mode Setting) by using the radeon.modeset=0 boot parameter (see above). If I don't do this then I have poor video playback (a strange vertical pixelation) and get low values in glxgears (you see "Software Rasterizer" written when running the command glxgears -info). So I need to disable KMS. Where do I insert this radeon.modeset=0 boot parameter? I'd tried inserting it in Yaboot.conf like this:```
boot=/dev/hda2
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
partition=3
root=/dev/hda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
    label=Linux
    read-only
    initrd=/boot/initrd.img
    append="**radeon.modeset=0 quiet splash**"

image=/boot/vmlinux.old
    label=old
    read-only
    initrd=/boot/initrd.img.old
    append="quiet splash"
``` and running sudo ybin -v and sudo reboot in terminal.
Also tried: putting ```
radeon.modeset=0 video=radeonfb:1024x768-24@60
``` or ```
Linux radeon.modeset=1 radeonfb:off
``` or ```
video=radeonfb:off
``` or ```
video=radeonfb:off radeon.modeset=0
``` or ```
nomodeset
``` in place of ```
radeon.modeset=0 quiet splash
``` Also running ```
echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf
``` in terminal.
But the problem remains.

Please help.

---

### Post by rsavage on 2012-03-07
I think you've exhausted most options there!  Your yaboot.conf looks fine.  I know it is a stupid question, but are you sure you have a radeon card?

I've been playing with lucid recently and it is the best IMHO.

Try

```

video=offb:off radeon.modeset=0

```

If you want to try with KMS on instead, use

```

video=radeonfb:off video=offb:off radeon.agpmode=-1

```When booted up use the command

dmesg | grep drm

If you only get a few lines of output then KMS is not on fully (even if it says it is enabled).

That is all I know.

---

### Post by Improntant on 2012-03-08
Thanks for the response. I'm pretty sure I have radeon, because lspci command in terminal returns Radeon 7500.  ```
video=offb:off radeon.modeset=0
``` didn't work. 
With ```
video=radeonfb:off video=offb:off radeon.agpmode=-1
``` dmesg | grep drm command only returned a couple of lines, like you predicted.
I'll try to install Ubuntu 12.04 when it is out.

**EDIT:**
**Solved**. Added ```
radeon.modeset=0
``` to yaboot.conf and then used _[this]("http://mac.linux.be/content/g4-emac-1ghz-radeon")_ xorg.conf file. It was possible to run non-pixelated video before using this fix, by using X11 video driver in media players or compiling the latest mplayer2 version from source, but this resulted in low frame rate playback.
The problem was that OpenGL was using Software Rasterizer, not hardware rendering driver. glxgears previously returned ~ 300 fps and now I get ~ 4100 fps. I also tried kubuntu 12.04 live cd and Software Rasterizer was in use. Now glxinfo | grep render returns: ```
direct rendering: Yes
OpenGL renderer string: Mesa DRI R100 (RV200 5157) 20090101 AGP 4x PowerPC/Altivec TCL
```My Xorg.conf file [http://pastebin.com/6xH79RUc](http://pastebin.com/6xH79RUc)

---

