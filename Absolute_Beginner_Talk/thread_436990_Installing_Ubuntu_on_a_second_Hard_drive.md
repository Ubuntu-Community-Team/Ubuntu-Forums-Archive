---
title: "Installing Ubuntu on a second Hard drive?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Mr|C on 2007-05-08
I'm installing Ubuntu, but I dont want to do it on my main hard drive, I want to do it on an external hard drive. (500GB). More than enough. Bought for a bargain to ;)

Anyway, is it possible, to install Linux on an external hard drive? If it is, how would I boot it up? Would I just plug the hard drives USB cable in, and it would load on boot?

Thanks to anyones help. 

<3

---

### Post by c0d4041292 on 2007-05-08
i havnt tried this yet but plug it in via usb and put the ubuntu cd in the cd-Rom drive. when u instal u should get the optio of installing to it. ima noob so if it doesnt see the external u will need to wait for a ubuntu master :grin:

---

### Post by Mr|C on 2007-05-08
> **c0d4041292 said:**
> i havnt tried this yet but plug it in via usb and put the ubuntu cd in the cd-Rom drive. when u instal u should get the optio of installing to it. ima noob so if it doesnt see the external u will need to wait for a ubuntu master :grin:

I know I can install it by putting in the Live CD, but I cannot recall whether I get the choice of where to install it to. If I do, how do I make Ubuntu boot from the HD, when it's connected and Windows when it isnt?

---

### Post by LaRoza on 2007-05-08
You can set the BIOS to boot from a specific device, if the device is not found it will go to the second, and so on.

The first boot device is usually a floppy drive (even if you don't have one), the second is the cd/dvd player, and then the hard drive and its partitions. USB devices can be easily set during startup. 

Even if you have more than one bootable drive, you can select any one at start up.

---

### Post by Mr|C on 2007-05-08
> **LaRoza said:**
> You can set the BIOS to boot from a specific device, if the device is not found it will go to the second, and so on.

The first boot device is usually a floppy drive (even if you don't have one), the second is the cd/dvd player, and then the hard drive and its partitions. USB devices can be easily set during startup. 

Even if you have more than one bootable drive, you can select any one at start up.

Is there anyway to set the order of the boot? For instance:
[LIST=1]
[*]My Hard drive
[*]Parents Hard drive
[*]Disk
[/LIST]

With that said, I'm guessing that if I put the Live CD in my CD Rom drive, I can choose where I install Ubuntu. (I seem to remember it auto installs in C:\)

---

### Post by Mr|C on 2007-05-08
Gah, need a fast answer. The hard drive I wnat to buy only has 40 minutes left before I have to wait 1 week to delivery :P

---

### Post by LaRoza on 2007-05-08
You can set the priority at set up. 

The exact method depends on the manufacturer.

You should keep the Floppy and Cd drive first, then you can select the devices.

the priority should be:

1. Floppy
2. Cd Drive
3. USB Disk
4. Hard drive (primary partition)

---

### Post by Terl on 2007-05-08
> **Mr|C said:**
> Gah, need a fast answer. The hard drive I wnat to buy only has 40 minutes left before I have to wait 1 week to delivery :P

Are you certain also that the pc will boot from a usb device?  Depending on how old it is, it might not...

---

### Post by Mr|C on 2007-05-08
> **Terl said:**
> Are you certain also that the pc will boot from a usb device?  Depending on how old it is, it might not...

My computer is relatively new. Probably the best of 2-3 years. Even if it doesn't boot, I'm [retty happy with the purchase.

---

### Post by Gmbrdilos on 2007-05-08
I think it all depends on your motehrboard

you should be able to configure boot device priority in your bios
some motherboards have the option to boot from USB some don't
it all depends on age

---

