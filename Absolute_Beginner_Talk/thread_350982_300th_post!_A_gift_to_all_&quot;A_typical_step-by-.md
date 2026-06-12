---
title: "300th post! A gift to all: &quot;A typical step-by-step install of Ubuntu&quot;"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by emarkay on 2007-02-01
It's been almost 6 months.  We've been through a lot (at least I have) here in Ubuntu-land.  So as my gift to all, while reinstalling Ubuntu 6.06 (Dapper) I documented the steps to do so.  This is a typical install on an older machine, and using an HP printer.  Your steps and choices may be different, but feel free to copy this and edit it for yourself.   

*Trust me, It will come in handy if you ever need to reinstall!*  ;)

*******
Reinstalling Ubuntu - 02/01/07

1. Set Desktop Background, Menus & Toolbars, Screen Resolution, Screensaver, Sessions,Theme.
2. Configure Language Support, Login Window, Software Preferences
3. Configure Nautilus (Home Folder) Edit Menus & Toolbar preferences.
4. Disable Thumbnails.
	a. System Tools/Desktop/Gnome/Thumbnailers.
5. Remove Games and unneeded Fonts, and add extra Fonts.
6. Add 686 Kernels (2.6.15.2 or later).
Reboot
7. Remove 386 Kernels.
8. Add Python QT3, Boinc
Reboot
9. Add user Directories and Downloaded files.
	a. Automatix - 
	b. HPLIP - 1.7.1 or later
	c. Seamonkey - 1.1 or later
	d. Java - 1.6.0 or later
	e. Flash - 9.0.31 or later
10. Run Update.
	a. (93 Updates, 130Mb)
Reboot
11. Install Automatix (Do not run at this time).
12. Configure FireFox
13. Configure Login screen resolution ("VGA=791" in /boot/grub/menu.lst)
14. Configure desired visible Disk volumes (/etc/fstab).
	a. Remove: hda1 (C), hda6 (F), hdb5 (G).
15. Run Update again.
Reboot.
16. Install and configure HPLIP.
17. Run Automatix
Reboot
18. Install and Configure Printers.
	a. Insure printer is on and connected
	b. In  terminal, go to appropriate directory and enter: sh ./hplip-1.7.1.run
	c. Select "A" (Automatic mode).
	d. The "Printer Setup Wizard" will appear now.
	e. Enter data as needed.
	f. Add any  additional printer configurations (Monochrome, Draft, Photo, etc.).  
		Use System/Administration/Printers.  
		NOTE: Select "Use another printer by specifying a port" option and its default entry!
	g. Select new printer and edit "Properties". (Paper size default is A4, for example.)
Note: Time to this point is approximately THREE hours.
19. Install and configure SeaMonkey, Java & Flash (See Separate Instructions!)
20. Profile Disk.
	a. Add "profile" in GRUB boot menu at end of "kernel" line. 
	b. Press "e" to edit, "e" to edit line, and enter "b" to reboot.
20. Copy files from /var/cache/apt for possible reload.

MRK

---

