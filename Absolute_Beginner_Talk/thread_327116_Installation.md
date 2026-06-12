---
title: "Installation"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by rkb280 on 2006-12-28
I am completly new to Ubuntu, I have been given 6.10.

I tried to install it today using K8 ASROCK K8NF6G-VSTA SK754 DDR PCX M-ATX motherboard,

as far as I can tell, Ubuntu does not recognise the LAN, and therefore will not get past the initial install, section.

Can't get on the internet.

What make, and model of Motherboard, can I use for Ubuntu?

Thanks

RKB

---

### Post by Iarwain ben-adar on 2006-12-28
Hiya,
if you have a spare NIC (preferably Realtek) lying around, use that :wink:

That should work :D


Iarwain

---

### Post by sartic on 2007-02-02
> **Iarwain ben-adar said:**
> Hiya,
if you have a spare NIC (preferably Realtek) lying around, use that :wink:

That should work :D


Iarwain

That's easy. What about VGA and sound onboard. Even Feisty can not handle this?!

---

### Post by Iarwain ben-adar on 2007-02-02
How do you mean, Feisty can't handle this? (note that Feisty is still beta)


Iarwain

---

### Post by steve.horsley on 2007-02-02
I am using a Gigabyte GA-K8NF-9 with an Athlon 3200+. And PCIe nVidia 6600GT. Everything is perfect except for the firewire port which I haven't tested as I don't have any firewire peripherals. 

Don't mix SATA and IDE hard drives though (My hard drive is SATA). IDE CD-ROM is not a problem, but mixed hard drives confuses the bootloader installer.

---

### Post by sartic on 2007-02-03
> **sartic said:**
> That's easy. What about VGA and sound onboard. Even Feisty can not handle this?!

I am not lammer. Ubuntu stable, unstable (6.10 :) and alpha beta whatever you call it doesn't recognise this mobo (vga, sound and lan is not recognised after installation)

---

### Post by tommcd on 2007-02-03
For the onboard nvidia video you will need to install the nvidia driver from the repos (nvidia-glx).
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)
Scroll down to "nvidia gforce 6 integrated."
I don't know why the NIC or audio are not working. They are both realtek.
[http://www.asrock.com/mb/overview.asp?Model=K8NF6G-VSTA](http://www.asrock.com/mb/overview.asp?Model=K8NF6G-VSTA)
For the audio, try working your way through this:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
For the NIC, do you get anything with <ifconfig eth0> in terminal? Did you try enableing eth0 under system>administration>networking?
EDIT: During the installation you should be able to select "configure networking later" or whatever it says. This should let you install it and then figure it out later. Sorry to ask, but are the LAN and audio properly enabled in the BIOS?

---

### Post by lamego on 2007-02-03
> as far as I can tell, Ubuntu does not recognise the LAN, and therefore will not get past the initial install, section.
The LAN card is not required for the initial install, so your problem is not related to it.
Have you tried booting from the alternate CD ?

---

