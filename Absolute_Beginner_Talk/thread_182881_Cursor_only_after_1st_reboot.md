---
title: "Cursor only after 1st reboot?"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by teebob21 on 2006-05-26
Ok, I am trying to install Ubuntu for the first time, and I am having major difficulties after the CD portion of the install. After the first stage of the install, the GUI says to remove the installation media and reboot. When I do, I come back only to a blinking cursor. I've tried to troubleshoot this in every way I know how.

I've tried both Ubuntu and Kubuntu distros on burned CDs that are md5 verified. The BIOS does recognize the HDD and is set to boot to it if no bootable CD is found. Please help me escape the windoze experience!

CPU: 1 Ghz Duron
RAM: 512 MB
HDD: 8 GB Hitachi
DVD: Toshiba 12x DVD
Video Card: Hercules 32MB AGP Generic

---

### Post by sinkxdie on 2006-05-26
What happens when you press "CTRl+ALT+F1-8?"

---

### Post by teebob21 on 2006-05-26
Not a thing.

---

### Post by sinkxdie on 2006-05-26
What color is the backround? Grey with stripes, or all black? Is this cursos white or black? Is it an X or a regular aarow?

---

### Post by teebob21 on 2006-05-26
The screen is all black with a flashing white cursor in the upper left, much as you see when you boot a computer with no disks attached. I checked, disks are attached and powered, with proper pin alignment on the IDE cables.

Also, I do know what the X GUI cursor looks like, as I've played around with Ubuntu at a buddy's. I'd love to be seeing it, but I've just got the standard one.

The install process was SO smooth, I don't think I could have goofed it up. It was the default install, not a server or expert config.

---

### Post by sinkxdie on 2006-05-26
Oh, you mean a cursor, for text, I thought you meant a mouse cursor.

Did you burn the .iso yourself?
Dif you maybe do a server install, or expert install?
Did you do that checksum thing for the iso if you burned it?(I dont know too much about it, google it):D

And also, did you get a bootsplash screen?

EDIT: more questions :D

What speed did you burn the .iso at, if you did?

Did you try a live CD yet? Does that work properly?

---

### Post by teebob21 on 2006-05-26
[QUOTE=sinkxdie]Did you burn the .iso yourself?[/QUOTE]
Yes.
[QUOTE=sinkxdie]Dif you maybe do a server install, or expert install?[/QUOTE]
No, default. See edit to previous post.
[QUOTE=sinkxdie]Did you do that checksum thing for the iso if you burned it?(I dont know too much about it, google it):D[/QUOTE]
Yes, md5 checksum verified. See parent post.
[QUOTE=sinkxdie]And also, did you get a bootsplash screen?[/QUOTE]
No, not after install. BIOS screen, then little unresponsive text cursor.
[QUOTE=sinkxdie]What speed did you burn the .iso at, if you did?[/QUOTE]
4x. Only speed that my burner will burn Linux discs without making a coaster.
[QUOTE=sinkxdie]Did you try a live CD yet? Does that work properly?[/QUOTE]
Not yet, I have a Knoppix CD around here somewhere, but I can't find it ATM. 

Edit: Damn Small Linux runs from CD.

---

### Post by sinkxdie on 2006-05-27
:( I think your problem is the video card.
Im going to go research it, but this forum is open for suggestions to help teebob :D

---

### Post by teebob21 on 2006-05-27
Thanks for all your help...I wondered if it was the vid card myself, but since the install GUI looked ok, I thought I might be in the clear with X too.

Thank you thank you thank you for helping.

---

### Post by confused57 on 2006-05-27
You could try pressing "Esc" when grub is loading to display the grub menu, then choose recovery mode, press "enter".

This should bring you to a prompt:

Type in:  dpkg-reconfigure xserver-xorg
Press "enter".

When it asks if you want Ubuntu to autodetect your video hardware, select "no", then try some different drivers, starting with "vesa".

You can probably select "default" for everything else, after selecting a driver.

Hope this helps, at least something to try...good luck.

---

### Post by Koech on 2006-05-27
It sounds to me like there is no hard disk in place, and since you are certain it is, then the only logical conclusion is that the boot loader GRUB is messed or confused. Try to reinstall GRUB before you think of a clean reinstall.
To reinstall GRUB look [here]("http://doc.gwos.org/index.php/Restore_Grub").

---

