---
title: "Can't Change IP Address on Printer"
date: 2013-04-20
forum: Any Other OS
---

### Post by altirisx on 2013-04-20
[IMG]http://i38.tinypic.com/20rmscl.png[/IMG]

This is an image of th printer settings on Linux Mint 14 Cinnamon. Where it says "IP Address" I want to change those long words to the IP Address of the printer howerver I cant click on it, when I go into Options the only option I have is "allow users". I installed the printer drivers and everything needed. Linux Mint 14 Cinnamon needs to update this.

I used to be able to do this on Ubuntu and Linux Mint 14 MATE, however on Cinnamon there doesnt seem to be an option for this. Is there any way I can edit this via a terminal, or edit a notepad file where this is stored?

Please respond ASAP. Thanks!

---

### Post by Perfect Storm on 2013-04-20
Moved to Other OS/Distro Support.

---

### Post by kurt18947 on 2013-04-21
The printer app in gnome-shell and Mint is very limited.  Luckily, the gnome 2 app is still available in repository and still used on Xubuntu.  It's called system-config-printer-gnome and once installed can be opened from terminal using "system-config-printer".    Launch the app, right-click the printer icon, select 'properties'.  'Device URI' is the printer address.

Cinnamon has made mostly good choices for apps installed by default.  Perhaps they'll re-think this;).

---

### Post by mips on 2013-04-21
[http://ubuntuforums.org/showthread.php?t=1967795](http://ubuntuforums.org/showthread.php?t=1967795)

---

### Post by altirisx on 2013-04-21
Thanks, I already had this installed (so I am guessing Linux mint installs the features but just doesnt use it....idk why, this has the most features). I just ran system-config-printer and it loaded up! Thanks!

---

