---
title: "Ubuntu 11.04 ASUS K42J Series NVidia Geforce 310M"
date: 2011-08-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by daniel02_0403 on 2011-08-16
Hi guys,

I'm using Ubuntu 11.04 64-bit and everything went well except for my graphics card driver.
I'm using an ASUS K42J Series laptop with an NVidia Geforce 310M graphics card.

Does anyone have an idea of how to fix the graphics card driver issue for the mentioned unit and specs above?

Thanks in advance for all those that would help.
Really need this fix ASAP.

---

### Post by Ubunting biochemist on 2011-08-24
Sadly linux NVIDIA drivers do not yet support the 310M card (I am trying hard to wait patiently :) The normal linux video drivers that come with the install work just fine but the 3rd party NVIDIA drivers do not. I assume this is a fresh install, if so it is probably easiest to just wipe and reinstall again then DO NOT INSTALL THE NVIDIA DRIVERS. This should fix the problem. There is most certainly a way that this can be done in command line but I don't know how and it will probably be as painful as just doing a fresh install. Good luck!

---

### Post by papibe on 2011-08-24
I'm running 11.04 (Unity) on a Toshiba laptop with the Nvidia 310M card. It works perfectly. In my understanding it is supported:
```
$ grep 310M /usr/share/doc/nvidia-current/README.txt
    GeForce 310M                          0x0A70             C
    GeForce 310M                          0x0A72             C
    GeForce 310M                          0x0A75             C

```
That is under the list of supported cards. May yours have a different chipset? (check the hex numbers).

AFAIK, most of the problems with that card are related to [Optimus]("http://www.nvidia.com/object/optimus_technology.html") rather that the card itself.

I hope this helps,
Regards.

---

### Post by daniel02_0403 on 2012-04-16
How did you install the drivers sir?
Could you put it in details.
I've been with this for almost a year now.

Thanks.

---

### Post by papibe on 2012-04-16
Let's discard Optimus.

Could you post the result of this command?
```
lspci | grep -i vga

sudo lshw -C display
```
Regards.

---

