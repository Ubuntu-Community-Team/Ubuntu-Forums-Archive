---
title: "when do i install drivers for my nvidia card?"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by lopagof on 2007-05-21
before or after I put it (the card) in the system?

I will be using the nvidia geforce 4.

Im pretty handy with the terminal but I suck at installing drivers so any guides are okay.:KS

---

### Post by taurus on 2007-05-21
After you install the card.  Then, you can install the driver for it when you boot up your machine.

---

### Post by lazyart on 2007-05-21
install hardware, boot up and ubuntu will tell you that the xserver can't start.  log in textually.

type```
sudo dpkg-reconfigure xserver-xorg
``` and select the nv driver when asked.

type```
startx
``` when that's all done and you'll be in the gui.  go to system>administration>restricted drivers manager and you can install the nvidia driver there.

---

### Post by diskotek on 2007-05-21
i think it sounds better to install drivers before you mount gra&#287;hic card. you graphic card would be usable without nvdia drivers as i know.

---

### Post by FuturePilot on 2007-05-21
Wouldn't it be easier to do ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by lopagof on 2007-05-21
okay so...

would easyubuntu> install nvidia drives> turn off > hook up card > power on be the ideal option?

---

### Post by taurus on 2007-05-21
1.  Edit /etc/X11/xorg.conf and replace whatever Driver with "**vesa**". 

```
gksudo gedit /etc/X11/xorg.conf
```

2.  Shutdown the machine and install the new graphic card.

3.  Reboot and see if X is still working with vesa driver.
a.  If not, reconfigure X with

```
sudo dpkg-reconfigure xserver-xorg
```

4.  Install nVidia driver from synaptic.

---

### Post by lopagof on 2007-05-21
....on second thought lazyart sounds like he knows what he is doing.

---

### Post by lopagof on 2007-05-21
okay taurus tnx.

---

