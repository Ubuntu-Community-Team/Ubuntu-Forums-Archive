---
title: "Adjust LCD Monitir Brightness Jaunty"
date: 2009-09-14
forum: Art &amp; Design
---

### Post by elnegrito on 2009-09-14
Already posted this in the [General Help]("http://ubuntuforums.org/showthread.php?p=7928933&posted=1#post7928933") forum but didn't get much help. So I'll try posting it hear.

Any idea on how to adjust the LCD monitor brightness in Ubuntu 9.4 (Jaunty)?

It used to be (on Ubuntu 8.4) as easy as typing "echo -n 00 > /proc/acpi/video/VGA/LCD/brightness" in a terminal. Where 00 was the desired value. I used to use 86 as the value of choice. Using this setting was the only way to get the photos that I edited with The Gimp or any other image editor to appear as bright as on my screen.

Unfortunately on Jaunty the "/proc/acpi/video" folder is empty and the command returns an error.

I also tried following the instructions on this post, but that didn't work ether.

I understand that the "prints to dark" situation is quite common when using LCD monitors but I do a fear amount of image editing and the earlier mentioned code worked just perfect for me. It makes no difference if I printed the images at home or at those one hour photo printers. The difference in color/brightness was, at least for me, unnoticeable.

Any Ideas? At least whats the "/proc/acpi/video/VGA/LCD/brightness" equivalent in Jaunty?

My system is a desktop (not a notebook) with an MSI Socket AM2+ Motherboard (AMD 790X (ATI RD780) Chipset & ATI SB600 Chipset) AMD 3GHz dual core CPU (Athlon 64 X2 6000+), 4GB ram an ATI Radeon graphics card (256 GB) and Dell 17" LCD Monitor.

Any help much appreciated!

---

### Post by foxmulder881 on 2009-09-14
Excuse my ignorance, but why don't you just adjust the brightness via the LCD displays built in buttons?

---

### Post by elnegrito on 2009-09-14
Sounds as the most logic answer. But incredible as it sounds the monitor brightness is at 0% and still, when printing edited photos, things appear darker than on the monitor. Believe me it drives me crazy.

The big problem is when I sent pic's to a printer though there web interface if I print at home i can alway adjust the printer settings, and if i personally go to the printer the images can be adjusted to some extent (trial and error)at the kiosk. But I really want to make a photo book at one of those web sites that print them but trial and error with a $30 plus book doesn't sound cost efficient.

---

### Post by Newfoundlander on 2009-09-15
Go to Add/Remove apps and install the "Monitor Settings" or "DisplayCalibrator" and see if one of those let you adjust your monitor.

---

### Post by foxmulder881 on 2009-09-15
> **elnegrito said:**
> Sounds as the most logic answer. But incredible as it sounds the monitor brightness is at 0% and still, when printing edited photos, things appear darker than on the monitor. Believe me it drives me crazy.

Yeah I can understand that. I'm a Photographic Imaging Professional and believe me, I know how annoying it is to have your display not calibrated to your printer.

---

### Post by elnegrito on 2009-09-16
Newfoundlander,
The DisplayCalibrator may just do the trick unfortunately, I ran out of ink to test the results.

foxmulder881,
At lest someone can feel my pain.

---

### Post by Toshibawarrior on 2009-09-16
Yep, DisplayCalibrator is good, and I completely forgot about it. Anyway, I guess your best bet is to find someone with a printer to test the results. Or wait until you can buy new ink for your printer....which is a fairly useless and obvious advice. I guess there's no way around it. :(

---

