---
title: "Couple of easy questions....I hope!"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by dmorand on 2007-07-15
Ok I'm hoping these are easy to answer.  

1.  How can I modify my boot options so I don't have to do it everytime I start my computer?
I always have to change the boot options from "... quiet splash" to "...quiet noapic".

    - Where can I go to modify this?

2.  I installed Envy to get my Nvidia Go 6150 drivers, and now it's running in 1024X768, but I have a widescreen display on my laptop.  How do I go about getting it to run in widescreen?

---

### Post by Arisna on 2007-07-15
1.)  You would change those boot options in the configuration file /boot/grub/menu.lst.  Open it by pressing Alt+F2 and entering "gksu gedit /boot/grub/menu.lst" in the box that appears.  Scroll down near the bottom of the file.  You'll see something that looks like this.  You want the topmost one.  The part of interest to you is bolded.

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=6298d626-0a8f-4373-812
8-3037bbd46575 ro **quiet splash**
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

Make your edit, save the file, and you shouldn't have to manually edit that anymore at boot.  Note that you may have to repeat this process after each kernel upgrade.

2.)  Have you tried changing your resolution through your desktop environment (GNOME, I'm assuming) and through the ATI Catalyst control center?

---

### Post by nwadams on 2007-07-15
i don't know about #1 but this should help for #2
to change that you have to edit your /etc/X11/xorg.conf file
first make a backup ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
then open your xorg.conf file ```
sudo gedit /etc/X11/xorg.conf
```
near the bottom where it shows the following (note info may be different for you)
> 
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce 7600 GS"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

beside all of the resolutions you have to add the resolution you want, so if you want 1280x1024 then you add "1280x1024" to them all (i know you want widescreen, i'm just amking an example

then save and exit
then press ctrl+alt+backspace to restart X

before restarting X write the following command down
if your X blows up and wont' start use the following command to put your backup back in
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

remember linux is case sensitive

hope this helps

---

### Post by dmorand on 2007-07-15
Excellent, thanks to both of you!!!  I now have my grub modified and my resolution set to 1280x800

---

### Post by testube_babies on 2007-07-15
> **Arisna said:**
> 1.)  You would change those boot options in the configuration file /boot/grub/menu.lst.  Open it by pressing Alt+F2 and entering "gksu gedit /boot/grub/menu.lst" in the box that appears.  Scroll down near the bottom of the file.  You'll see something that looks like this.  You want the topmost one.  The part of interest to you is bolded.

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=6298d626-0a8f-4373-812
8-3037bbd46575 ro **quiet splash**
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

Make your edit, save the file, and you shouldn't have to manually edit that anymore at boot.  Note that you may have to repeat this process after each kernel upgrade.

Note:   you can avoid re-editing menu.lst on each kernel upgade by adding your desired boot options to the #defoptions line.

---

