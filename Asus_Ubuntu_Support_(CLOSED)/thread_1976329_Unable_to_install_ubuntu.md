---
title: "Unable to install ubuntu"
date: 2012-05-08
forum: Asus Ubuntu Support (CLOSED)
---

### Post by alexeyum on 2012-05-08
Hi,

I am trying to install ubuntu on my new notebook from flash-drive and the installer fails to load.

Detailed description:
Computer is ASUS N53S (Core i7, GeForce GT630M).
I create an installation flash drive (for ubuntu 11.04) using ubuntu 11.04 on another computer. Then I insert the flash drive, reboot the notebook and enter bios settings. I move the flash drive to the top in the priority list (however it appeared in the list only when I enabled the UEFI support option). Then I reboot the notebook and GRUB with 3 options (try ubuntu / install ubuntu / check disk) appears. I choose "install" (or "try"), the screen becomes black (though with a backlit) and nothing happens. The flash drive shows that it is in use for several seconds. I've tried to wait around an hour but still nothing happens. I also tried installing 12.04 version but the result was the same.

So... can't find the way to install it :(.

Thank you in advance.

---

### Post by lukeiamyourfather on 2012-05-08
Try the alternate install disc. It uses a text based installer which bypasses any graphics problems that would otherwise hold things up during the install process.

[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

---

### Post by alexeyum on 2012-05-08
Tried alternate installs for both 11.04 and 12.04.
Now GRUB suggests: Install Ubuntu / Install in expert mode / Check disc for defects / Rescue a broken system. Both 'install' and 'install in expert mode' result in the same behaviour.

---

### Post by lukeiamyourfather on 2012-05-09
What is the last line of text that you see when the installer hangs?

---

### Post by alexeyum on 2012-05-09
It hangs immediatly after choosing option in GRUB, not showing any text.

---

### Post by alexeyum on 2012-05-10
Installation was successful using DVD-disc (problem solved). However I wonder what was wrong with flash-drive..

---

### Post by snipe2004 on 2012-05-29
Alexeyum, could you tell me how Ubuntu manages to use your nVidia GT630M ? I have the same GPU, and so much trouble with it (and so, 3D games and visual effects on the desktop)... Thanks in advance

---

### Post by Dan Again on 2012-05-30
Problem is not the flash drive, it is with UEFI. I don't enough to explain the problem, but I had to deal with this when installing to my Zenbook (no CD drive). Some Google magic will probably turn up a more helpful answer.

---

### Post by Toasty27 on 2012-07-09
> **alexeyum said:**
> Installation was successful using DVD-disc (problem solved). However I wonder what was wrong with flash-drive..

Are you certain that you booted the disk under UEFI? (i.e. selecting the UEFI: option for the cd/dvd)

I've tried booting the Live CD and I still get a black screen after selecting an option in GRUB. I've tried booting both the regular CD and the alternate version from a flashdrive, like you initially tried, but (unsurprisingly) neither worked. I haven't tried the DVD version though (from what I understand, it just includes extra language support. I don't see how that would effect the boot process). I might try booting the alternate installer from a CD next.

I can boot fine in BIOS mode and install successfully, but no dice with UEFI so far. No matter what I've tried, I just get that black screen after GRUB.


Also, to any repliers, BIOS mode is not an option.

---

### Post by RaZoRbelarus on 2012-08-11
> **Toasty27 said:**
> Are you certain that you booted the disk under UEFI? (i.e. selecting the UEFI: option for the cd/dvd)

I've tried booting the Live CD and I still get a black screen after selecting an option in GRUB. I've tried booting both the regular CD and the alternate version from a flashdrive, like you initially tried, but (unsurprisingly) neither worked. I haven't tried the DVD version though (from what I understand, it just includes extra language support. I don't see how that would effect the boot process). I might try booting the alternate installer from a CD next.

I can boot fine in BIOS mode and install successfully, but no dice with UEFI so far. No matter what I've tried, I just get that black screen after GRUB.

Also, to any repliers, BIOS mode is not an option.

I have the same problem. And my laptop is almost the same as topicstarter's: Asus N53SV(i5+GT540M).
Ubuntu 12.04_amd64_desktop/alternate won't run in UEFI mode. And it is all working well in BIOS mode. No matter what I tried, it just hangs with black screen and even not responding to Ctrl+Alt+Del. Switching between CD and Flashdrive doesn't make any difference. Trying different boot parameters doesn't help either.
I'm currently downloading i386_desktop variant to see if it works.

Added.
It seems that i386 variant doesn't have UEFI support at all...

---

### Post by alexeyum on 2012-08-25
> **snipe2004 said:**
> alexeyum, could you tell me how ubuntu manages to use your nvidia gt630m ? I have the same gpu, and so much trouble with it (and so, 3d games and visual effects on the desktop)... Thanks in advance

 I'm not running any heavy graphics on Ubuntu, so I just don't know.

> **Toasty27 said:**
> Are you certain that you booted the disk under UEFI? (i.e. selecting the UEFI: option for the cd/dvd)

I have only global option "UEFI support" in BIOS and it was enabled.

---

