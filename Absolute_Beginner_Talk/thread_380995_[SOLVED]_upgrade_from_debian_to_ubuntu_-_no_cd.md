---
title: "[SOLVED] upgrade from debian to ubuntu - no cd"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-03-10
Hi

I hope I am not asking the same question again. I have recently managed to install debian from 2 floppies using the internet, making my ancient win98 machine (no cd or usb) dual boot debian / win 98 using the instructions here:

[http://www.debian.org/releases/stable/i386/](http://www.debian.org/releases/stable/i386/)

I then tried to follow these instructions:

[http://ubuntuforums.org/showthread.php?t=29358](http://ubuntuforums.org/showthread.php?t=29358)

I had to play a bit to get the floppy bootable.

The first time I ran it I seemed to get in a conflict with GRUB from the previous install, so I restarted from the debian boot disks, got as far as partitioning my disks, and then rebooted the machine with the ubuntu network floppy in.

All seemed to be going well with the ubuntu install until, having got to the second part of the install (after the initial packages had been loaded: debootstrap, various partitioning tools etc) the system again tried to initialise my network card (which it had successfully found for the first part of the install). It then just hung (blue screen).

I feel as though I must be over-complicating this. I surely shouldn't have to rebott to a win98 startup disk if I have a functioning debian install?

I'm at a loss, all help welcome.

Thanks

---

### Post by Kobalt on 2007-03-11
You shouldn't have to get back to a win98 boot, but you may have to start off again with a brand new installation of Ubuntu, that would be my advice...
The howto you followed is a bit old, I suggest you take a look at [this method]("http://www.ucc.asn.au/services/ubuntu.ucc") of net install for Ubuntu, this will get you a more up-to-date approach.

---

### Post by ubername on 2007-03-13
> **Kobalt said:**
> You shouldn't have to get back to a win98 boot, but you may have to start off again with a brand new installation of Ubuntu, that would be my advice...
The howto you followed is a bit old, I suggest you take a look at [this method]("http://www.ucc.asn.au/services/ubuntu.ucc") of net install for Ubuntu, this will get you a more up-to-date approach.

Thanks for this. I don't have an ethernet cable which will reach Perth, Australia from the UK, or have I missed something?

---

### Post by konungursvia on 2007-03-13
I would stick with Debian. It may be your hardware. It's almost the same as Ubuntu. Just learn to use it and download the packages you want for it, you'll be rocking. Debian is older but may install on a wider variety of older hardware. There is no guarantee that ubuntu can even recognize some of your old hardware. my 2 cents.

---

### Post by ubername on 2007-03-15
> **konungursvia said:**
> I would stick with Debian. It may be your hardware. It's almost the same as Ubuntu. Just learn to use it and download the packages you want for it, you'll be rocking. Debian is older but may install on a wider variety of older hardware. There is no guarantee that ubuntu can even recognize some of your old hardware. my 2 cents.

Thanks for this. I suspect you're right, but it still feels odd that I can't (and I emphasise the 'I') manage to do some sort of boot from floppy to get, via the network, a ubuntu install.

FWW I don't think debian is picking up my old AWE64 card anyway, which I will pursue as a separate activity, so it's not really about hardware support, I think I am just trying to understand what you can and can't use to get ubuntu installed.

---

