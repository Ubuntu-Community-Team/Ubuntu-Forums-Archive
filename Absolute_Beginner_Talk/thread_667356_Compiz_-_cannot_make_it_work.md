---
title: "Compiz - cannot make it work"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by lduplantie on 2008-01-14
I would like to experiment with desktop effects. However, I cannot get them to work on my PC:

Hardware: Intel Pentium III 1GHz (256KB), 512MB, 20GB IDE HDD, Desktop (4x4), Intel 815e, 48x CD-ROM,16x DVD+/-R, IIntel Pro/100 VE Ethernet (AGP4x slot empty), Viewsonic VA520 LCD monitor

Here is the terminal output of Compiz:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:1132 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

Thanks

---

### Post by Borbus on 2008-01-14
Which graphics card do you have? If you are on Nvidia then you simply need to install the Nvidia drivers, after that Gutsy should automatically enable compiz-fusion.

If you are unfortunate enough to be an ATI user then you have to try installing some ATI drivers, use Envy for this, and then use XGL or AIGLX. But when I was on ATI I couldn't get it to work.

---

### Post by lduplantie on 2008-01-14
I only have the onboard graphics. Intel 815e driver.

---

