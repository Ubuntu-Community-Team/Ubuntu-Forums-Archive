---
title: "Black screen booting ISO on 2016 MacBook Pro (MacBookPro13,1)"
date: 2016-11-07
forum: Apple Hardware Users
---

### Post by ramseygurley on 2016-11-07
Hi all,

I just received a new 2016 MacBook Pro "escape edition" (the one with Fkeys) and booting from the USB stick is not working. I get to the screen that allows me to choose to Try Ubuntu without installing/Install Ubuntu/OEM install, but when I hit enter the screen goes black and ubuntu never comes up. I tried Try and Install, on Ubuntu 16.04.1 and 16.10. Pressing 'c' puts me on the grub command line, so it seems to be working. I've verified my download shasum, and verified the shasum after writing the ISO to the USB stick.

Anyone have ideas about what's going on?

Thanks

---

### Post by howefield on 2016-11-07
Thread moved to "*Apple Hardware Users*" forum.

---

### Post by ramseygurley on 2016-11-07
I've tried editing the command before booting and changed "quite splash" to "nomodeset quiet splash" to no effect.

---

### Post by guinea2 on 2016-11-07
I would recommend just erasing the USB  installing the ISO to the USB again and see what happens, if that still doesn't work, I don't really know what would be causing it except for the USB stick itself or the computer. I would try a different USB though if reinstalling the ISO on the usb doesn't work.

---

### Post by ramseygurley on 2016-11-07
Hi guinea2, thanks for the suggestion. I verified the USB stick is good for 16.04.1 and 16.10 using

sudo dd if=/dev/disk2 bs=2048 count=778240 | shasum -a 256

The shasum on the stick matches the shasum for the downloaded file. I'm beginning to think there's something in Apple's EFI that's blocking it. I set gfxpayload=text and changed "quiet splash ---" to "debug nosplash --verbose", but I still get a black screen on F10. Still trying to read up on grub2 to see if I can get it to dump a log or just anything to give me a better idea why it isn't loading the linux kernel.

My problem sounds identical to [https://ubuntuforums.org/showthread.php?t=2303621](https://ubuntuforums.org/showthread.php?t=2303621) but there's no solution there.

I just tried Fedora 24 and I'm getting the same behavior. I get to the grub2 UEFI menu, but if I select any option, the screen goes black and I need to force reboot.

---

### Post by matsepp on 2016-11-08
Hi,
Same model, same problem, including Arch linux installer as well.
I read somewhere that people have had trouble in the past with MBP that included two graphic cards and the wrong one (not connected to the laptop screen) was used.
Did someone try with an external screen ?

---

### Post by ramseygurley on 2016-11-08
I just got Ubuntu 16.10 to boot into try ubuntu. The magic kernel param is nointremap. Source:  [https://ubuntuforums.org/showthread.php?t=2303621&page=2&p=13547523#post13547523](https://ubuntuforums.org/showthread.php?t=2303621&page=2&p=13547523#post13547523)

Aaaand, the keyboard seems dead. Okay, well, progress. External keyboard seems to work.

So far, keyboard not working, trackpad not working, and the SSD isn't visible in the installer. I should probably start a new thread and mark this solved.

---

### Post by david.romanos on 2017-02-15
Hey! Any update? Just bought a MacBook Pro 2016 13' no-Touchbar and I'm having the same exact problem.

---

### Post by lucperte on 2017-05-28
> **david.romanos said:**
> Hey! Any update? Just bought a MacBook Pro 2016 13' no-Touchbar and I'm having the same exact problem.

Me too same problem with my MBP 13 no toucHBar.

---

### Post by lucperte on 2017-05-28
Ubuntu installer don't see [FONT=Helvetica Neue]APPLE SSD AP0256J [/FONT][FONT=Helvetica Neue]PCI-Express[/FONT]

---

### Post by kevin160 on 2017-06-02
The latest kernels (after 4.4) seem to handle efi booting differently.  I wonder if the "noefi" option would help as it did me on an ancient MacPro.  Sounds like you were locking up exactly where I was.  To be clear,  do use the EFI version of Ubuntu, but pass it the "noefi" kernel option via grub.

---

### Post by lucperte on 2017-06-10
Thanks Kevin,
but it don't work. :evil:

---

