---
title: "[SOLVED] Missing Battery Applet in Kubuntu"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by regomodo on 2007-08-08
I've just installed Kubuntu on my laptop and the power-management applet was there.  Now it has disappeared and it is not available in the list of available applets to add to the panel. 

Where has it gone?

---

### Post by apetresc on 2007-08-08
The battery status applet is part of the "gnome-applets" package. Did you remove that for some reason?

Try reinstalling it with apt.

---

### Post by Hospadar on 2007-08-08
it's not going to be in gnome-applets since you are using kde

try installing/reinstalling klaptopdaemon.  If that doesn't add it to the applet list (or it's already installed), it might be something that runs in the system tray.  Try running klaptopdaemon from the command line.

If that opens it up, add klaptopdaemon to the startup programs

---

### Post by regomodo on 2007-08-09
> **Hospadar said:**
> it's not going to be in gnome-applets since you are using kde

try installing/reinstalling klaptopdaemon.  If that doesn't add it to the applet list (or it's already installed), it might be something that runs in the system tray.  Try running klaptopdaemon from the command line.

If that opens it up, add klaptopdaemon to the startup programs

cheers. i didn't get it to work as you said as it wouldn't work right.

klaptopdaemon returned with nothing in konsole so i searched for it in aptitude. Said it wasn't installed. Installed it and then ran the command again but still did nothing. Did a restart and the icon is back on the tray. It's not the same one as it doen't have the same icon and doesn't show the details like it used to but it'll do.

I had looked around beforehand but all i could find kde-guidance-powermanager. Installed that but did nowt. Need to remove it.

Don't know why klaptopdaemon removed itself. All i did was install htop, firefox, pidgin and added acpi=force to grub's menu.lst. Weird.

---

