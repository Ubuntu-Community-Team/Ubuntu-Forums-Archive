---
title: "unable to boot after update"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by screwey on 2007-04-30
Hi, this is the situation:

A few days ago i tried to update my ubuntu edgy to the new feisty release. Something went wrong during the update though, not everything was updated it seems. Now I am unable to boot. When i try to boot i just get the splashscreen, and the loading bar stops right at the begininng. I tried to enter the console, but it won't load either. When i enter the grub boot screen, I see the following kernels:

Ubuntu, kernel 2.6.17-11-generic
Ubuntu, kernel 2.6.17-11-generic (recovery mode)
Ubuntu, kernel 2.6.17-10-generic
Ubuntu, kernel 2.6.17-10-generic (recovery mode)
Ubuntu, memtest86+

I used the live CD to boot, to check if my drives where properly connected and if they were recognised by the system. They all appeared in gparted correctly, so i dont think that the hardware is the problem.

My recovery skills are quite minimal, as is my knowledge of linux, so if anyone has an idea how to fix this, plz help :)

thx

---

### Post by Seisen on 2007-04-30
How did you try to update, what i mean is which method did you use?

---

### Post by screwey on 2007-04-30
I changed my sources list for the apt-get tool, changed all the "edgy"s to "feisty"s.
Then i executed apt-get upgrade, apt-get dist-upgrade?

thx for the quick reply btw :)

---

### Post by Seisen on 2007-04-30
Can you boot into recovery mode at all?

---

### Post by screwey on 2007-04-30
I can't boot anything really, only from the live cd.
When i try to run recovery mode the system stops at
begin: Waiting for root file system ... ...

---

### Post by screwey on 2007-04-30
now it says:

Done.
ALERT! /dev/sda1 does not exist. Dropping to a shell!

Busybox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)

/bin/sh: can't access tty; job control turned off
(initramfs)



sda1 is my primary partition, on a sata controller, when i booted from live cd there was no problem mounting this drive, and it was visible as /dev/sda1

---

### Post by Seisen on 2007-04-30
I know another stupid question, it won't let you boot into the other kernel or recovery mode either?

---

### Post by screwey on 2007-04-30
nah, the same happens for the other kernel, also in recovery mode :)

---

### Post by Seisen on 2007-04-30
Try reinstalling Grub from the live-cd here are the steps [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")

---

### Post by GrueTamer on 2007-04-30
This happened to me a while ago, when I was using Edgy, and I'm afraid that the only solution that I can think of is a fresh install.  I believe that the cause of both your problem and mine was a kernel upgrade, and that also caused a problem with someone else I know, so maybe that screwed everything up.  But I could be wrong.

---

### Post by screwey on 2007-04-30
now when i try to boot the recovery mode of the 2.6.17-10 kernel, it stops at "setting up console font and keymap"
al the other stuff seems to be loaded ok, so i don't think its a problem with grub?

---

### Post by screwey on 2007-04-30
Now when i run the recovery mode of the 2.6.17-10 it freezes at "setting up console font and keymap"
So i dont think its a problem with grub, everyting else is loaded normally it seems to me?

---

### Post by stevekl on 2007-04-30
I have the exact same problem; bumping.

---

### Post by jome on 2007-05-02
I changed my usplash-artwork.so and after that did something like "dpkg-configure ..." and now /dev/sda6 has disappeared in ubuntu, not in windows!

---

