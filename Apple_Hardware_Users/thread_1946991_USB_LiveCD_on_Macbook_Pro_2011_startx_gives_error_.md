---
title: "USB LiveCD on Macbook Pro 2011: startx gives error &quot;No Screens Found&quot;"
date: 2012-03-25
forum: Apple Hardware Users
---

### Post by wyager on 2012-03-25
After much effort, I finally managed to create an Ubuntu 11.10 (64 Bit) liveUSB that works natively on my Macbook Pro. However, I am now stuck at the command line, and unable to boot the GUI.

Running "startx" or "sudo startx" prints out some stuff, then gives the error "no screens found". 

I assume the following fact may be very important: I used the option **nomodeset** in my grub.cfg. It is the only option that seemed to work. i915.modeset=1 only gets me as far as the purple loading screen, where the boot process freezes. Nomodeset gets me all the way to the command line. I assume this new issue also has something to do with the integrated Intel graphics.

Here is the entry in my grub.cfg that boots properly:

```
menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash nomodeset --
	initrd	/casper/initrd.lz
}
```

Does anyone have any advice for what I might try next? Is there anything I can post that would make this easier to debug?

---

### Post by mörgæs on 2012-03-26
Moved to the Apple forum.

---

### Post by wilfriedd on 2012-03-26
You just have to put this in your xorg.conf:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fbdev"
EndSection
```

than run startx

This worked for me on 2 separate MacBooks together with nomodeset :)

The problem is that you are probably booting via EFI. There currently are some problems with the video card drivers which expects a BIOS environment, and this can not be easily fixed without kernel patches. (see into the  Macbook Pro 8,1 + Maverick thread if you are interested) When you use this fix, X uses the efi framebuffer as video device. As a consequence, you will have only 2D, but you will have a working live environment.

---

### Post by wyager on 2012-03-26
> **wilfriedd said:**
> You just have to put this in your xorg.conf:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fbdev"
EndSection
```

than run startx

This worked for me on 2 separate MacBooks together with nomodeset :)

The problem is that you are probably booting via EFI. There currently are some problems with the video card drivers which expects a BIOS environment, and this can not be easily fixed without kernel patches. (see into the  Macbook Pro 8,1 + Maverick thread if you are interested) When you use this fix, X uses the efi framebuffer as video device. As a consequence, you will have only 2D, but you will have a working live environment.

That appears to have worked! I am currently working on modifying the LiveCD to include this. Thank you very much!


I have only recently started using Unix/Linux in any comprehensive fashion, so I am still learning a lot of stuff. I appreciate the help! I'll check out that thread in a bit.

---

### Post by mörgæs on 2012-03-26
Good, then please mark the thread 'solved'.

---

