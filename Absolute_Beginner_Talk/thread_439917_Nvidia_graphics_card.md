---
title: "Nvidia graphics card"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by G_force on 2007-05-11
It seems to be common but i have found a solution.

i installed 7.04
and it detects the onboard graphics chip instead of the PCI graphics card (/X11/xorg/ nVidia TNT/TNT2)
(i cannot disable the onboard graphics)

How do i get ubuntu to use the PCI as the graphics card.
(btw i have to use the recovery console to get anywhere as after the boot screen, the screen goes blank)


Thanks in advance

---

### Post by fjf on 2007-05-11
I have an nvidia card and I got the drivers installed by installing automatix ([www.getautomatix.com)](www.getautomatix.com)).  I know no geek should do it this way, but I come from windoze and I am no geek at all ;)

---

### Post by MoxJet on 2007-05-11
Did you try

sudo apt-get install nvidia-glx

?

---

### Post by G_force on 2007-05-11
yeah i have, but it detects the onboard device not the pci device thus when i do that the Xserver crashes and i have to restore the backups.

any more ideas

---

### Post by MoxJet on 2007-05-11
Hmm, post the output of lspci and your /etc/X11/xorg.conf ?

---

### Post by G_force on 2007-05-11
i would post it but i have no way of copy+pasting it

I just know that it detects the onboard graphics chip (intelll blah blah blah)
Then it uses the "i810" driver

I want it to uses the Nvidia TNT/TNT2 and the nvidia driver

when i run lspci it shows the video card

---

### Post by ajgreeny on 2007-05-11
Can you disable the on-board graphics in your bios?  If so that should do it.

---

### Post by fjf on 2007-05-11
If you cannot disable the onboard video from the bios try flashing the BIOS to the last version.  That Might allow you to disable it.

---

### Post by mstlyevil on 2007-05-11
There is one of two ways you can get the pci card to work. (The second option is a work around for the bios if the option to disable them is not there.)

1. If your bios has an option to disable the onboard graphics just use that option.

2. You will have to point xorg.conf to the particular pci slot the card is in.

For example your xorg.conf file will have to look something like this.

```
Section "Device"
        Identifier      "NVIDIA Corporation NV44 [Quadro NVS 285]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection
```

You will have to set the BusID to exactly match where you video card is installed. After that the nvidia driver will work.

---

