---
title: "Start up: video mode not supported"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by blag on 2006-11-06
Grub 'unpacks' and starts loading the kernel successfully. 

While the kernel is loading (before x starts, I assume), my LCD monitor displays the text 'VIDEO MODE NOT SUPPORTED' until the display mode is changed. 

I installed SVGATextMode only to find that my chipset is not listed in TextConfig. But besides this, I wouldn't know what file to edit to have the kernel change the display setting while it's loading. 

I'm thinking the next step would be to try fbset, but again, I'm not sure how to alter the boot routine to have the VGA mode set properly (differently?) during start up. 

Ctrl+Alt+F1 has the same problem: "VIDEO MODE NOT SUPPORTED". And I experienced the same problem while waiting for the installation CD to load.

---

### Post by PrairieShaman on 2006-11-06
You will probably need to install the right packages for your specific video card to have Ubuntu run in graphical mode. This will need to be done by your terminal, as far as I know. I had this problem when upgrading to Edgy, but I fixed it by installing nvidia-glx in the terminal, because my video card is an NVidia card. 

That's all the help I will be, im a nooblet too!

---

### Post by ReaderRat on 2006-11-06
Please run this code in Terminal and post the output.
```
sudo gedit /etc/X11/xorg.conf
```
and we will see what's up.

---

### Post by blag on 2006-11-09
Just thought someone might find this useful. I've resolved this issue:

I had installed Ubuntu version 6.06 (Dapper Drake) when I first posted. For that installation, I had to add "vga=791" (to change the boot time display settings) as one of my boot parameters in grub's config file /boot/grub/menu.lst. (791 seems to be a safe default, one site recommends trying 795 and downward)

I've recently installed Ubuntu 6.10 (Edgy Eft) and it does not suffer from the same problem. 

Now, onto figuring out why I can't use a resolution higher than 1024x768 (even after adding my preferred resolution to xorg.conf), and getting 3d acceleration to work. 

Thanks to all for such timely replies.

---

