---
title: "Booting usb with grub"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by HybridTheory on 2008-01-17
Hi i was wondering if you could use grub to boot from a usb cd drive my bios is not so great and doesn't pick up Usb drives yes I have turned on my usb setting but oddly it only picks up flash drive :mad: any clue? I've tried a really stupid set up...

### END OF WINDOWS LIST

# This is a divider, added to separate the menu items below from the windows
# ones.
title		DVD-USB
root            (hd1,0)
kernel          /boot/media/cdrom2

it doesn't hurt to try =]  (I've tried a few other set ups but they have failed to) 

thanks

---

### Post by ukripper on 2008-01-17
you can create usb flash  bootable 
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

works for gutsy too.

---

### Post by HybridTheory on 2008-01-17
Thats for booting from a usb flash drive I need a way to boot from the USB dvd drive I have ubuntu installed lol I'm just wondering if you could set the grub to boot from usb dvd to install other OS's that only fit on DVDs like Mac or windows MCE and such thanks tho =[

btw the usb thing its picking up is my psp lmao.. with a 512MB memory card ...idk how my bios is on drugs

---

### Post by ukripper on 2008-01-17
> **HybridTheory said:**
> Thats for booting from a usb flash drive I need a way to boot from the USB dvd drive I have ubuntu installed lol I'm just wondering if you could set the grub to boot from usb dvd to install other OS's that only fit on DVDs like Mac or windows MCE and such thanks tho =[

btw the usb thing its picking up is my psp lmao.. with a 512MB memory card ...idk how my bios is on drugs

this may help [http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/](http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/)

---

