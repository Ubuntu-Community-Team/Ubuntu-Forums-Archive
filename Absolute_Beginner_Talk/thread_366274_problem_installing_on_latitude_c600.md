---
title: "problem installing on latitude c600"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by killaray on 2007-02-20
im tryin to install ubuntu on my cousins dell latitude c600.. although its old it has enough to run ubuntu

1ghz processor and 512 ram

so i couldnt get the live cd to run properly, i did check the other posts ive found on this issue and all say to use the noapic or noacpi commands (but they dont work)... anywho ive used the alternate cd and installed ubuntu, now it wont fully boot or when it miraculously does itll freeze like 5 minutes in... anyone know wut the issue might be? ive updated the bios and all that good stuff... any help?

---

### Post by killaray on 2007-02-20
anyone?

---

### Post by R3linquish3r on 2007-04-22
Disable **acpi** and enable **apm**. The easiest way to do this is to open **/boot/grub/menu.lst**

When looking at this:

```
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,1)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/hdc5 ro quiet splash
initrd          /initrd.img-2.6.17-11-generic
quiet
savedefault
boot

```

At the end of the kernel line after **splash** add **acpi=off apm=on** and reboot.

BTW: I'm currently running Feisty on my Latitude C600 with 800Mhz and 128 RAM :)

---

### Post by n3tfury on 2007-04-22
> **R3linquish3r said:**
> Disable **acpi** and enable **apm**. The easiest way to do this is to open **/boot/grub/menu.lst**

When looking at this:

```
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,1)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/hdc5 ro quiet splash
initrd          /initrd.img-2.6.17-11-generic
quiet
savedefault
boot

```

At the end of the kernel line after **splash** add **acpi=off apm=on** and reboot.

BTW: I'm currently running Feisty on my Latitude C600 with 800Mhz and 128 RAM :)

nice, i'll try that before the boot process.  i could not get Feisty (beta) or Final to boot on my C600.  which windows manager are you using on yours?

---

### Post by R3linquish3r on 2007-04-22
I'm using Gnome. However I always use the Alternate install with whatever I'm doing. Never really liked the Live install for some reason :/

---

### Post by n3tfury on 2007-04-22
thanks man.  i was thinking of going gnome on mine but then installing fluxbox.  was just curious of the performance mostly.  :D

---

### Post by R3linquish3r on 2007-04-22
I've actually been swapping between the two. Sometimes I feel like Flux sometimes I feel like Gnome. I'm surprised I'm not a woman lol.

---

### Post by n3tfury on 2007-04-22
lol, well if you have no problems running both, i'm going to install it tonight to check it out.  (already have it on desktop)

---

### Post by R3linquish3r on 2007-04-22
GO for it. This thing will even run KDE :P

---

