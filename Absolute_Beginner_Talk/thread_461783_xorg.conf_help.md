---
title: "xorg.conf help"
date: 2007-06-02
forum: Absolute Beginner Talk
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

### Post by freefromXP on 2007-06-02
I can't help you with the xorg.conf except maybe using Envy to install the ati driver.

   I would suggest using Xubuntu with XFCE desktop, it  will run a lot faster and smoother on that sys.  You can install it and try it.  You will have both and can just change session to the one you prefer.

To install Xubuntu-desktop

sudo gedit /etc/apt/sources.list


Uncomment the universe repository lines by removing the # that begins each of those lines. Do not uncomment the narratives in that file.  And the restricted once that should be on top.
Examples

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main **restricted**
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main** restricted**
eb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty **universe**
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty **universe**

  May not look just like that and may have more or less

sudo aptitude update

sudo aptitude upgrade

sudo aptitude install xubuntu-desktop

log out and change session to XFCE you should see a huge difference.  Not has pretty and stuff as ubuntu but will run and work really nice on that sys.

---

### Post by richaoj on 2007-06-02
Yea . . . I have xfce as well . . it does run slightly better - ubuntu (gnome) doesn't run all that terrible either, but after all of this work at getting this system up and running, i want everything to be perfect.  maybe i'm just a little ocd.

thanks for the help

---

