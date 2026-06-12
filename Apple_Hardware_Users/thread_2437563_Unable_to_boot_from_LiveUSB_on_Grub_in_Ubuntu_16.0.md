---
title: "Unable to boot from LiveUSB on Grub in Ubuntu 16.04"
date: 2020-02-25
forum: Apple Hardware Users
---

### Post by marielaas on 2020-02-25
Hello everyone! 

I'm a newbie to Linux and Ubuntu in general and I got an old Macbook and had Ubuntu installed onto it. I wanted to try to try out some other distros of Linux to possibly dual boot other OS' but when I enter into Grub, I'm unable to view the option to boot from USB. I installed Manjaro onto my USB to try it out and I was able to try it out on a Macbook and Windows OS to see if it was able to show and see if it worked and it worked perfectly. Is there something I need to change onto Ubuntu in order to allow booting from USB on the Grub menu?

---

### Post by howefield on 2020-02-25
Moved to the "*Apple Hardware Users*" forum.

---

### Post by gsahli on 2020-02-26
Can you give us more detail about what you have done?
What model of Macbook (usually something like "Late 2008" and "MacBook 5,1")?
Did you follow any instructions to make the USB a bootable one? 
like:
[https://wiki.manjaro.org/index.php/Burn_an_ISO_File](https://wiki.manjaro.org/index.php/Burn_an_ISO_File)
and did you run sudo update-grub with the USB inserted (so grub can find it)?

---

### Post by CelticWarrior on 2020-02-28
USB media usually boots (or don't) from the firmware (UEFI), not Grub. It should happen before Grub.

I'm not familiar with Macs and how they boot installation media but given the model as requested above, someone will certainly be able to help you.

---

### Post by este.el.paz on 2020-02-29
@marielaas:

If the shasum numbers checked out on your iso file for manjaro, you should be able to boot the USB by restarting nd holding the "alt/option" key down to bring the OSX boot manager window up, then the various disks should show up there, select the "EFI boot" option for Manjaro and it should boot it up . . . .

---

### Post by marielaas on 2020-03-22
> **este.el.paz said:**
> @marielaas:

If the shasum numbers checked out on your iso file for manjaro, you should be able to boot the USB by restarting nd holding the "alt/option" key down to bring the OSX boot manager window up, then the various disks should show up there, select the "EFI boot" option for Manjaro and it should boot it up . . . .

This solved my problem everyone! Thank you so much for your help! Sorry for the lack of response. Life has been hectic these past few weeks. Decided to stick with Ubuntu and absolutely loving the new update.

---

### Post by este.el.paz on 2020-03-22
> **marielaas said:**
> This solved my problem everyone! Thank you so much for your help! Sorry for the lack of response. Life has been hectic these past few weeks. Decided to stick with Ubuntu and absolutely loving the new update.

Thanks for the post back on it . . . pretty basic stuff, glad it worked out for you . . .  Manjaro is a pretty good system, seems fairly zippy, etc.

---

