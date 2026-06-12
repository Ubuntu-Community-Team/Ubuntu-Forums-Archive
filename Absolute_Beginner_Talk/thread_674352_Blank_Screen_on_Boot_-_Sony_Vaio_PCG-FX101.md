---
title: "Blank Screen on Boot - Sony Vaio PCG-FX101"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by jdennis_99 on 2008-01-21
I have installed (I think :confused:) Kubuntu 7.10 on my Sony Vaio PCG-FX101 using the alternate installation CD. I tried the LiveCD, but even when I added the boot parameter 'acpi=off' (as discussed in some forums), it showed a Kubuntu loading screen which was eventually replaced by a blank screen.

So I used the alternate installation CD. I used the 'acpi=off' boot parameter, and it went into the text-based installer, all of which ran through fine. The system rebooted, went through GRUB and then loaded that good old blank screen again.

I *think* it has actually loaded Kubuntu, because when I press the Power button, it shuts down. I understand from some of the posts on similar threads that it's probably caused by a graphics driver incompatibility, but I can't figure out how to fix it!

I have tried using the 'vga=xxx' and 'acpi=off' boot parameters using GRUB with many variations, with no success. I have also tried to use the recovery mode which is available via the GRUB boot menu, but to no avail. I can't actually get the system to boot up, even to a command line. The closest I can get is a hung system with a flashing cursor.](*,)

Sony Vaio PCG-FX101
512MB RAM
10GB Hard Drive
Intel Celeron 600MHz Processor
Intel 815EM Chipset Graphics
13.3" XGA TFT 1024x768

As far as I can tell, my system meets the minimum requirements. It's probably a school-boy error, but I can't do anything with it at the moment. Any help would be appreciated!

---

### Post by jdennis_99 on 2008-01-21
SUCCESS!!

I managed to load the command line interface using the recovery option on the GRUB menu. I had to edit the command line parameters by adding 'acpi=off' and 'vga=ask'. I then booted and chose option 4 from the VGA menu. It then went through a load of text junk for about a minute (looks like old MS-DOS stuff, please forgive the crude analogy) and gave me a command prompt.

I managed to load pico to edit the menu.lst file. That took me a while - I misread it as menu.1(one)st, if that makes any sense. Please forgive another crude analogy, but this seems to be an equivalent of autoexec.bat and config.sys on old MS-DOS/Windows 3.x systems. I have edited the recovery option to include 'acpi=off vga=0F05' so that I can boot to a prompt with minimum fuss. I have also edited the standard option to get rid of the  'ro quiet splash' replacing it with 'nosplash acpi=off vga=0F05'.

The standard option went through all the textual nonsense and then went to the blank screen - but the text it came up with just before is something to do with KDM, which as my vague understanding goes, is something to do with Kubuntu's GUI, KDE. This would again seem to indicate a problem with the graphics driver. The good thing was that once I got to this blank screen, I could get to a command prompt by pressing Ctrl+Alt+F2.

I then typed 'sudo dpkg-reconfigure xserver-xorg' which allowed me to select the Intel 815EM graphics driver!! Excellent. A reboot gave me - GUI!! HOORAY!!

OK, it looks like I didn't need any help after all. Well, if anyone else needs help installing onto a Sony Vaio PCG-FX101, they can use this as a guide.

---

### Post by spiderbatdad on 2008-01-21
take a look at /etc/usplash.conf and see if it is compatible with your supported resolution.

---

