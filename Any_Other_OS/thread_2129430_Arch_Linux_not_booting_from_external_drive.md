---
title: "Arch Linux not booting from external drive?"
date: 2013-03-26
forum: Any Other OS
---

### Post by sparksaus on 2013-03-26
So my current setup is like this: my laptop has two hard drive bays. In the first bay, I have a hard drive with Ubuntu (my main OS). In the second, Windows. I use Grub2 to boot into both (installed on the first drive, naturally).

I installed Arch Linux on a third hard drive I have lying around as I want to experiment with it. I have an external bay that I can plug it into but when I try to boot (after update-grub), I get some error about the kernel not being loaded. But if I take out my Windows hard drive and put in the Arch one, it loads fine. I've been looking all over and have yet to find a decent answer to my problem. It's probably worth noting than I have no bootloader installed on the Arch drive. 

Can anyone point me in the right direction for booting the external drive?
It also might be worth noting that I have installed bootloaders before but they made no difference so I formatted and reinstalled without.

---

### Post by Hodevah on 2013-04-03
I am no expert but would it be possible that booting off from an external hard drive might be the problem?
Maybe Arch is not able to recognize the fact that it is booting off from the external hard drive and as such is having problems booting from it as evidenced by your statement that outside of the internal hard drive it has problems and when you switch it over to your internal hard drive, it boots fine. Just a thought.

I was always under the impression that trying to boot an operating system from an external hard drive was, regardless of the operating system being used, was kind of a difficult thing.

---

### Post by bfmetcalf on 2013-04-03
Arch can be booted off of a USB drive just fine.  Check your /etc/fstab and make sure you are using UUID to specify where everything is mounted for a start.  But this sounds much more like grub doesn't know exactly where the kernel is to boot it.  I am gonna say you may have to check out your grub.cfg and edit something like changing a /dev/sdx to a UUID.

Edit:  The way I do it is to install arch to the usb drive and put grub on that drive. Then boot from the external drive, I have never tried it with the grub on the main drive to load the OS from the stick.  I can tell you that the grub on the USB drive can boot other OS's on the internal drive just fine for sure.

---

