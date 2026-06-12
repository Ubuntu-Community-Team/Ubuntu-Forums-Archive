---
title: "[SOLVED] UbuntuStudio"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by acowboydave on 2007-07-01
Hello, installed Ubuntustudio on Feisty,and a dual boot with XP. On the startup boot I got a new kernel called Lowlatency 2.6.20-16 since it is the first one listed of three linux kernels, unless I choose the generic it starts automatic with that. The problem is it hangs when it fails to load wfb module, does not exists, and it fails to load the nvidia module. Loads fine with the generic though. Can I remove it? or repair it.

---

### Post by mkoehler on 2007-07-01
In order to edit the GRUB menu, you can type the following command:

```
sudo gedit /boot/grub/menu.lst
```

This will allow you to modify the options that are listed on the grub menu and/or their order.

---

### Post by starcraft.man on 2007-07-01
> **acowboydave said:**
> Hello, installed Ubuntustudio on Feisty,and a dual boot with XP. On the startup boot I got a new kernel called Lowlatency 2.6.20-16 since it is the first one listed of three linux kernels, unless I choose the generic it starts automatic with that. The problem is it hangs when it fails to load wfb module, does not exists, and it fails to load the nvidia module. Loads fine with the generic though. Can I remove it? or repair it.

You have to reinstall the nvidia drivers for the low latency kernel (there is integration to a certain extent from what I know), its sufficiently different from your old one that it doesn't work unless its reinstalled in that. I'd advise booting up with the nv driver (you can edit the xorg from recovery mode, if you don't know how say so), installing your cards drivers again and restarting. If any other problem persists we can deal with that. The low latency driver offers advantages to those doing a lot of AV work (I think), so if you intend to do that I assume you'd want to fix it.

To edit xorg for nv, just boot into recovery mode and apply this command:
```

sudo nano /etc/X11/xorg.conf
```

then scroll down the list until you see an entry labelled "device nvidia" or something like that.
Look for driver and make it "nv" (if it still fails to boot, make it "vesa" by same process. Then save it by pushing Ctrl + O (not number), enter, and then Ctrl +X for quitting nano editor. Then issue this command:

```
sudo reboot
```

Then load up with the kernel and install drivers again.

Edit: Oh and if you want to edit the grub options, I will give you further instructions on that after. Please don't edit that unless you know what your doing (i.e. what your changing), you can be left with an unbootable system.

---

### Post by acowboydave on 2007-07-01
Hello, thanks to the fast response, I can get to desktop using the generic 2.6, that's no problem. To tell you the truth I don't know how to edit xorg from recovery. Real new

---

### Post by starcraft.man on 2007-07-01
> **acowboydave said:**
> Hello, thanks to the fast response, I can get to desktop using the generic 2.6, that's no problem. To tell you the truth I don't know how to edit xorg from recovery. Real new

Ok then, I'll give you the graphical way. I thought I was step by step enough... GUI it is.

Open a terminal. Paste the following in:

```
gksudo gedit /etc/X11/xorg.conf
```

This will bring up the text editor. Scroll down until you see this section, your mileage will of course vary, mine is a 6800 GT yours probably isn't. Drive line is whats important in blue.

```
Section "Device"
        Identifier      "nVidia Corporation NV40 [GeForce 6800 GT]"
[COLOR="Blue"]        Driver          "nvidia"[/COLOR]
        BusID           "PCI:1:0:0"
EndSection

```
Replace "nvidia" with "nv" (and in the case that fails, unlikely as it is, repeat this step and switch to "vesa").

Push the save button, that overwrites the old and saves a backup to the same directory.

Reboot the machine, and select the regular low latency kernel. Boot into it and log in. Then go get [Envy]("http://albertomilone.com/nvidia_scripts1.html") (or if you prefer, whatever other way you previously installed driver) I'm sure ya can get those in again. Then, if you did it manually repeat above process to change driver back to nvidia or if you used envy its automatic. 

Reboot and log in again and you will be done. Hope thats enough.

---

### Post by acowboydave on 2007-07-01
Fixed, thanks for all the help. :D

---

### Post by starcraft.man on 2007-07-01
> **acowboydave said:**
> Fixed, thanks for all the help. :D

No problem, please remember in future when you change kernels (mostly when its a drastic change, sometimes updated kernels are fine) things that integrate (proprietary drivers like nvidia, VM drivers like VBox Vmware and other kernel additions) need to be reinstalled or resetup. This same process will always get you booting though, and from there you can reinstall everything that caused a problem.

Glad to help, have a nice day. Don't forget to put SOLVED at the end of the title (edit original post) and then others know your fixed and other folk can consult your problem for solution.

---

### Post by acowboydave on 2007-07-01
Thanks again

---

