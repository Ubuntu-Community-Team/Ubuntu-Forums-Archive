---
title: "Bootloader must have crashed, can i get it back ?"
date: 2014-07-07
forum: Any Other OS
---

### Post by CARLYN on 2014-07-07
Hi, I had Win7 and Mint running so that whenever i turned on PC i used the arrow keys to decide what to boot. I wrecked it by running UbnuntuStudio with a USB stick in Persistanse mode. didnt even know what that meant but it ran great of the usb STICK. Then when I tried to reboot nomally it justs hangs with a white dash on an otherwiswe blank screen.

Is there a tool I can download to fix this or anyway ?

---

### Post by ajgreeny on 2014-07-07
Running ubuntu as a live persistent system should not have affected your bootloader in any way, so I suspect you must have done something else to kill whatever it was that booted your system.

Were you using grub, or did you use either easybcd, or perhaps install Mint with their version of Wubi, ie within your running Windows 7?

If this was a normal partitioned install of Mint using grub it is quite likely that Boot-Repair from my signature may help you restore grub.

---

### Post by grahammechanical on 2014-07-07
It is possible that when you installed Ubuntu Studio to the USB memory stick you did not notice that Grub was going to be installed into the MBR of sda. Now, with the USB stick removed grub cannot find its boot configuration files because they are on the USB stick.

Try booting with the USB memory stick in the port and then selecting Linux Mint. If Mint loads remove the USB stick and in a terminal run

```
sudo update-grub
sudo grub-install /dev/sda
```

and that will put the Grub of Linux Mint into the MBR of sda.

Regards.

---

