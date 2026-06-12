---
title: "Enable graphic driver in live cd without reboting"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Wikzo on 2007-10-19
I am playing around with the live cd of Ubuntu 7.10 on my home computer. Can't install it yet because of something RAID on my hard drive ...

I wanna test Compiz Fusion effects, but then I have to download and install some drivers for my nVidia Geforce 6800 card. The installation goes well, but then I have to restart and everything are gone.

Is there any way to enable the graphic drivers in live mode **without** rebooting the system?

---

### Post by Hospadar on 2007-10-19
After installing and configuring the driver,

You'll need to go to a terminal (use ctrl-alt-F1)
and restart your xserver (the gui) with ```
sudo /etc/init.d/gdm restart
``` (the command is slightly different if you are using kde, I think it's kdm instead of gdm)
this should plop you back into your gui if all goes well, if not, try a ctrl-alt-F7 to get back to the virtual terminal where the gui is normally stored.

---

### Post by FredB on 2007-10-19
> **Wikzo said:**
> I am playing around with the live cd of Ubuntu 7.10 on my home computer. Can't install it yet because of something RAID on my hard drive ...

I wanna test Compiz Fusion effects, but then I have to download and install some drivers for my nVidia Geforce 6800 card. The installation goes well, but then I have to restart and everything are gone.

Is there any way to enable the graphic drivers in live mode **without** rebooting the system?

You can't without installing the system on your computer.

---

