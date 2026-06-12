---
title: "Mac boot order problem on Uni Macbook... HELP!!!!?"
date: 2008-04-06
forum: Apple Intel Users
---

### Post by ThingsThatGoFlirInTheShla on 2008-04-06
I've borrowed a macbook from University and was unable to use the internet on it at home so I ran my Ubuntu (feisty) live CD on it instead.
I accidentally clicked on "boot from first hard disk" on one of my Ubuntu boots and now I can't start OSX Tiger.
I have to hand the Macbook back tomorrow and I was wondering how I can restore the boot order (if that's what's wrong).

---

### Post by cyberdork33 on 2008-04-06
I don't know why that would cause a problem.

---

### Post by ThingsThatGoFlirInTheShla on 2008-04-07
It's causing a problem because I would like OSX to boot automaticaly as it would on a regular, single boot macbook.
At the moment I can only run Ubuntu on it and have no idea how to boot into OSX.
I just want it to be able to boot OSX when  I press the power button.

---

### Post by SergioA on 2008-04-07
Hi!

When turning your Mac on, hit "Alt" when you hear the "gong" and keep it pressed until you see the choice of which system to boot from; choose OSX and is System Preferences restore the default boot for OS X

Let me know!

Ciao

Sergio

---

### Post by cyberdork33 on 2008-04-07
I meant, I do not know why / how choosing "boot from hard drive" would cause something to break... it literally just passes control back to the primary bootloader on the drive. I would try as stated in the last post. Holding "ALT" should list all the bootable partitions available.

---

### Post by mrsteveman1 on 2008-04-07
Choosing "boot from first hard disk" would likely just jump to the code in the first 446 bytes of the MBR for that disk, and since OS X doesn't install any such code (it would be useless), i don't know that it would hurt anything for the firmware to try and execute it.

It also shouldn't have changed the NVRAM variable in the firmware that controls which disk is used for startup, so rebooting the laptop should boot back into OS X, if it doesn't something else is wrong.

Holding option/alt at boot should bring up the OS chooser, if that doesn't work something else is obviously wrong

Are you seeing just a flat grey screen at boot? What about the darker grey apple in the middle of the screen?

---

