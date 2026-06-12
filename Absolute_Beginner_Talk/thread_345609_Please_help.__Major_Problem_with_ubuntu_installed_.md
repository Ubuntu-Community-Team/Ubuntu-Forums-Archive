---
title: "Please help.  Major Problem with ubuntu installed on external HD."
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by The-Master on 2007-01-24
Well I installed Ubuntu on an external hard drive and that was all fine.  I restarted the computer and then unplugged my harddrive and got a GRUB 21 error.  I crapped myself.  I thought I had broken my computer.  So I frantically plugged my hard drive back in and rebooted.  It came up with a menu with what OS to boot.  Ubuntu or Windows.  Now this _only_ comes up if I have my external hard drive is plugged in, otherwise I get the error.  My did is pissed off because he doesn't like this added annoyance and I am also annoyed as I have to keep my hard drive plugged in which was not the point in having an external hard drive.  Does anyone know how I would stop this happening.  I am willing to get rid of ubuntu it is so annoying. Thanks.

---

### Post by Rippey on 2007-01-24
to restore ubuntu boot from a with the external drive and in a console type "grub-install /dev/sd*" where * is your drive letter (probably a)
to restore windows repair the boot record with a windows cd.
do it in this order or ubuntu won't boot (you will be able to restore ubuntu with a live cd aswell if you realy need to get windows to work first)
after you've done that you can start windows from you normal settings to start ubuntu you'll have to boot from usb, just a simple setting in your bios

---

### Post by The-Master on 2007-01-25
> **Rippey said:**
> to restore ubuntu boot from a with the external drive and in a console type "grub-install /dev/sd*" where * is your drive letter (probably a)
to restore windows repair the boot record with a windows cd.
do it in this order or ubuntu won't boot (you will be able to restore ubuntu with a live cd aswell if you realy need to get windows to work first)
after you've done that you can start windows from you normal settings to start ubuntu you'll have to boot from usb, just a simple setting in your bios
My computer did not come with a windows cd so what can I do?  Thanks.

---

### Post by Rippey on 2007-01-27
what do you use to reinstall windows?

---

### Post by louieb on 2007-01-27
> **The-Master said:**
> My computer did not come with a windows cd so what can I do?  Thanks.
Just Google:
```
restore windows mbr
```
and you find a way or 2 or a 100.

---

### Post by confused57 on 2007-01-27
Here's an excellent guide to restore your Windows mbr(you'd need to create a Win98 boot floppy):
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You might want to try Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

see the section on "Situations where Super Grub Disk is useful"...it's only about a 1 mb download that you burn to cd.

---

### Post by Tomosaur on 2007-01-27
Boot has two stages. The first runs off the MBR, which is why Grub still loads when you don't have the HD plugged in. Unfortunately, the second stage is stored on the Ubuntu root partition, which is why you're getting the error if you unplug the HD. The solution would be to create an Ubuntu root partition on the same hard drive as the NTFS drive (thus meaning Grub will load safely every time), OR to put Windows on the external HD, and Ubuntu on the internal.

Since your dad is annoyed, perhaps you should explain to him that the computer cannot load without a boot loader. The Windows one is 'invisible' so to speak, unless you enable it from within Windows. You can make the Windows bootloader 'see' Ubuntu - so that it gives you the option of booting to it if and when you choose. Check [this page](http://highlandsun.com/hyc/linuxboot.html) for more information.

However, you need a windows XP recovery disk to reinstall the Windows bootloader, since Grub is currently installed over it.

You can also download [Grub for Windows](http://www.geocities.com/lode_leroy/grubinstall/), which should fix your problem.

---

