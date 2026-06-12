---
title: "Ubuntu 12.04/12.10 on Macbook Pro 8,2. From BIOS-mode  to EFI"
date: 2012-09-23
forum: Apple Hardware Users
---

### Post by proycon on 2012-09-23
I've been running Ubuntu in BIOS-compatibility mode for a year now, but the ATI radeon card is quite power hungry and the noise of my fans spinning at max to compensate started to bother me. 

I thought I'd share my experiences in getting  Ubuntu 12.04 to work on a macbook pro 8,2 (15") in **EFI-mode** rather than BIOS-compatibility mode. The advantage is that only then the integrated card becomes available. I in fact set it up to use only this integrated card (intel) only and disabled the ATI radeon card.  I'm **not** doing a fresh install but working with my **existing** installation. 

Since several patches would be needed to get the video card to function properly with the current kernel shipped with Ubuntu 12.04, I simply upgraded the kernel to the newest 3.5 for the upcoming Ubuntu 12.10: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5.4-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5.4-quantal/) , download and install all packages for your architecture (including the linux-headers-all package). Should work fine on 12.04.


Rather than remove grub-pc (bios) and have only grub-efi I kept it installed and attempted to build the (64-bit) efi application on the side, so I can boot in both modes. For your convenience, I put the full resulting contents of my /efi/grub/ dir (on the OS X partition!!) here: [http://download.anaproy.nl/grubefi.tar.gz](http://download.anaproy.nl/grubefi.tar.gz). You can put this on the Mac OS X partition (/efi/grub). Make sure to edit the grub.cfg in-place there and verify it points to the right partition and kernel. reFIt/reFInd will pick it up and show an entry in the boot menu. 

Below is my grub.cfg configuration for efi. The i915 options are important as otherwise you're likely to stare at a blank or purple screen as soon as you boot, one of the most common and challenging problems I faced:

```

set timeout=10

insmod part_gpt
insmod ext2
insmod font

set debug=video
insmod efi_gop
if loadfont unicode.pf2
then
	insmod
	gfxterm
	set gfxmode=auto
	set gfxpayload=keep
	terminal_output fgxterm
fi

set root='(hd0,gpt4)'
menuentry "Linux (EFI, without bios dump, no radeon)" {
  search --file --no-floppy --set=root /vmlinuz
  fakebios
  set gfxpayload=keep
  # Switch gmux to IGD 
  outb 0x728 1 
  outb 0x710 2 
  outb 0x740 2 
  #Power down ATI 
  outb 0x750 0
  linux /boot/vmlinuz-3.5.4-030504-generic root=/dev/sda4 video=efifb i915.modeset=1 i915.lvds_channel_mode=2 i915.lvds_use_ssc=0
  initrd /boot/initrd.img-3.5.4-030504-generic
  sleep 2
}

```

What doesn't work yet:
 - Suspend
 - External Monitor (not possible with intel card afaik, needs radeon)

What does work:
 - everything else (wifi, cam, sound), also:
 - 3D acceleration (compiz). You may need to delete your old xorg.conf if you get no acceleration yet. Output from glxinfo should be:

```

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 

```

Recommended links:
 - [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
 - [http://ck.kennt-wayne.de/2012/jun/gentoo-linux-on-the-macbook-pro-82-late-2011](http://ck.kennt-wayne.de/2012/jun/gentoo-linux-on-the-macbook-pro-82-late-2011)
 - [http://dentifrice.poivron.org/laptops/macbookpro8,2/](http://dentifrice.poivron.org/laptops/macbookpro8,2/)
 - [https://help.ubuntu.com/community/MactelSupportTeam/EFI-Boot-Mactel](https://help.ubuntu.com/community/MactelSupportTeam/EFI-Boot-Mactel)

Next challenge:
 - See if I can get the radeon to work as well and try vga-switcheroo

---

### Post by pete-woods on 2012-09-23
I'm very interested to see how successful you are in getting both graphics cards working in hybrid mode. Given Ubuntu 12.10 is using Xorg 1.13 and all the graphics drivers have been updated to support this, it seems like it could be made to work!

---

### Post by proycon on 2012-09-23
Suspend is now also working for me, I followed the instructions from [http://dentifrice.poivron.org/laptops/macbookpro8,2/](http://dentifrice.poivron.org/laptops/macbookpro8,2/) , which compiles a small fixgpu program and hooks it in pm-utils.

Hybrid mode will be next :)

---

### Post by pelle.k on 2013-05-30
Thanks for the work you've done. I wouldn't advice editing grub.cfg directly though because grub.cfg is rewritten everytime update-grub is called, which can be quite often. So this what you do:

Modify (or replace) *line 11* in **/etc/default/grub** to this (bold is new);
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet **video=efifb i915.modeset=1 i915.lvds_channel_mode=2 i915.lvds_use_ssc=0** splash"
```
Add this to *line 179* in **/etc/grub.d/10_linux** (bold is new);
```

   sed "s/^/$submenu_indentation/" << EOF
[B]     # Switch gmux to IGD
     outb 0x728 1
     outb 0x710 2
     outb 0x740 2
     # Power down ATI
     outb 0x750 0[/B]
 }

```

Now, if you run;
```
sudo update-grub
```
/boot/grub/grub.cfg should be updated (and stay that way).

---

### Post by pelle.k on 2013-05-30
Also, i did install macfanctld in the hope that my MBP would stay as cool as when running OSX, but it doesn't. I wouldn't say it super hot, but you can feel the difference allright. Any tips on further optimization?

---

