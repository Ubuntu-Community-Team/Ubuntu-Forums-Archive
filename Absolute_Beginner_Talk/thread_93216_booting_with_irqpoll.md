---
title: "booting with irqpoll"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by -::Bas::- on 2005-11-21
Does anyone know how to install ubuntu with the irqpoll option, cuz i'm seeing something like this when i install kubuntu:

irq15: nobody cared (try booting with "irqpoll" option.
handlers:
[<d48994a0>] (ide_intr+0x0/0xed [ide_core])
Disabling IRQ #15

---

### Post by Kyral on 2005-11-21
You just need to add the option to the bootline

Open up menu.lst with

```
sudo gedit /boot/grub/menu.lst
```

And go down to the lines with "kernel" starting, and just add "irqpoll" to the end of it (I wish I could show you mine right now but I am not at my computer).

Feel free to paste it in if you want us to double check

---

### Post by -::Bas::- on 2005-11-21
When I give in that command you suggested I get the message that the "sudo kernel could not be loaded from the image" or something similar..

As well with the Ubuntu image as with the Kubuntu image.. 

I type the command when the Ubutu-logo appears for the first time, and I am asked to choose between server or desktop install.

I'm really sorry, but I am a complete Linux n00b. I want it badly, I really want to get rid of the MS-junk.. Please give me more advice how to solve this.
i am on a pc with the following specs:
-mobo: MSI RS480M2 (ATI RS 480)
-cpu:   AMD XP 64 3000+
-2 x 512 ddr ram

Is my mobo interfering??

---

### Post by Ndlovu on 2005-11-29
Not sure if you've figured out a solution yet, but I was given the same message when I booted up after upgrading from HoaryHedgehog (5.04) to BreezyBadger (5.10). I think it's a problem with the kernel not recognising my CD drive for some reason. I managed to boot by using an older kernel at startup. When the system boots, press [ESC] to bring up the boot menu (there should be a prompt for this, but it only lasts like a second so it's easy to miss). Try selecting an older kernel and see if that works (there should be options). I used 2.6.10-5-386 which worked for me. Not sure where to go from there though...

---

### Post by Kyral on 2005-11-29
Yah I should mention that it only seemed to happen to me when I was using a custom kernel...

---

