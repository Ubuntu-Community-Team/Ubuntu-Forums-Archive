---
title: "How to install on external HDD?"
date: 2009-11-25
forum: Apple Hardware Users
---

### Post by Romu on 2009-11-25
Dear all,
I left Ubuntu for some months now, tired of fighting against my Mac when tried to get Ubuntu working.

But, I'll never quit Ubuntu completely. And I would like to test 9.10 on an external HDD (connected through USB) but that doesn't seem to be possible.

On previous Ubuntu versions (and on my previous Macbook Pro 2.1), when getting the partition phase of the installer, I had the choice to installe on the local HDD or on the USB connected HDD.

When I try 9.10 on my new Macbook Pro (5.3 I guess, june 2009), the external HDD is well seen and mounted by the LiveUbuntu, but when trying to install, it is not proposed when getting the partition phase of the installer.

Any idea? Thanks.

---

### Post by dennis123123 on 2009-11-25
Macs wont boot linux from USB :(

Many forums etc agree. The only "kinda" method is to put the bootloader and kernel on a partition or CD and chainload the USB drive. Defeats the object if you ask me though...

---

### Post by linuxopjemac on 2009-11-25
firewire drives will do though....

---

### Post by Romu on 2009-11-26
> **dennis123123 said:**
> Macs wont boot linux from USB :(

Many forums etc agree. The only "kinda" method is to put the bootloader and kernel on a partition or CD and chainload the USB drive. Defeats the object if you ask me though...

If you were in France, I would show you a Macbook Pro 2.1 booting Linux on an USB HDD. No pb.

But I would appreciate your references on this assumptions, it's may be an explanation why I can't boot my Macbook Pro 5.3 like that.

---

### Post by dennis123123 on 2009-11-26
> **Romu said:**
> But I would appreciate your references on this assumptions, it's may be an explanation why I can't boot my Macbook Pro 5.3 like that.

Many forum posts etc, and personal experience (5,5 model)

eg:
[http://echochamber.me/viewtopic.php?f=20&t=20620#p611628](http://echochamber.me/viewtopic.php?f=20&t=20620#p611628)
[http://ubuntuforums.org/showthread.php?t=941240](http://ubuntuforums.org/showthread.php?t=941240) 
[http://www.everymac.com/systems/apple/macbook_pro/faq/macbook-pro-boot-from-external-firewire-or-usb-drive.html](http://www.everymac.com/systems/apple/macbook_pro/faq/macbook-pro-boot-from-external-firewire-or-usb-drive.html)


Reading the last one, you may have some luck with a GPT formatted disk... that is something I did not try yet.

---

### Post by Romu on 2009-11-27
Thanks Dennis,
Yes the partition table of the USB disk seems to be critical.

---

