---
title: "xorg.conf and powerbook g3"
date: 2007-06-02
forum: Apple PPC Users
---

### Post by richaoj on 2007-06-02
I have finally succeeded at installing ubuntu dapper on an old world powerbook g3 wallstreet   (300mHz, 512M RAM, 40 G hard drive, ATI 3D Rage LT PRO, Lucent Orinoco Silver PCMCIA card) !!!

I do not believe that my xorg.conf file is properly set though.  Rendering seems to be slow, especially when compared to OS9 on the machine.

lshw produces:
```

*-display

description: Display controller
product: 3D Rage LT Pro
vendor: ATI Technologies Inc
physical id:11
bus info: pci@00:11.0
logical name: /dev/fb0
version: dc
size: 16MB
sidth: 32 bits
clock: 33MHz
capabilities: bus_master cap_list fb accelerated
configuration: depth=32 driver=atyfb frequency=59.91 Hz mode=1024x768 visual-directcolor xres=1024 yres=768
resources: iomemory:820000000-82ffffff ioport:fe000400-fe0004ff iomemory:80000000-80000fff irq:24

```

What values do i need to put in when i reconfigure the xorg.conf file?
it asks for 

The video card's bus identifier: (i've tried PCI:00:11:0 --crashed the xserver)
Enter the amount of memory (in kB) to be used by your video card: (I assumed this would be size=16000kB)
Use kernel framebuffer device interface: (Yes)
. . . 
and a bunch of other stuff . . . non-relevant (to this particular question

can anyone help here?

---

### Post by gvigorus on 2007-09-19
Hey, please how did you get your Orinoco Silver to work?!?! Dying to get it working...

---

### Post by richaoj on 2007-09-20
I had to specify a certain io range in the kerenel parameters, as i recall, because of some bug in the kernel that let to two devices having conflicting values . . . lemme look into it, and i'll get back to you soon . . .

---

