---
title: "Fglrx cripples Kubuntu"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Keilious on 2007-12-06
After week of trying to get Kubuntu 7.10 64-bit onto my computer, the install finally went through properly.

First thing I've done is install the restricted drivers for my Radeon X1900XTX.
Surely enough, the driver sets my screen resolution just fine, but now everything is running ridiculously slowly! Even a click on the K-menu takes a moment to render.
Just about every drop down menu and text box constantly flickers too. :/
In addition, attempting to write up this thread caused everything but the wallpaper and the mouse to disappear (writing this up now on a different computer).

How am I to fix this?

Edit: Oh, and additionally, when I click Log Out now the box that appears only lets me log out, without the other options such as shut down and restart.

---

### Post by kellemes on 2007-12-07
> **Keilious said:**
> After week of trying to get Kubuntu 7.10 64-bit onto my computer, the install finally went through properly.

First thing I've done is install the restricted drivers for my Radeon X1900XTX.
Surely enough, the driver sets my screen resolution just fine, but now everything is running ridiculously slowly! Even a click on the K-menu takes a moment to render.
Just about every drop down menu and text box constantly flickers too. :/
In addition, attempting to write up this thread caused everything but the wallpaper and the mouse to disappear (writing this up now on a different computer).

How am I to fix this?

Edit: Oh, and additionally, when I click Log Out now the box that appears only lets me log out, without the other options such as shut down and restart.

You can check /var/log/Xorg.0.log for errormessages (EE)
Are you using Compiz or another composite manager? Or just KDE?
Have you installed XGL besides fglrx?

---

### Post by Keilious on 2007-12-07
> **kellemes said:**
> You can check /var/log/Xorg.0.log for errormessages (EE)
Are you using Compiz or another composite manager? Or just KDE?
Have you installed XGL besides fglrx?
After turning on Compiz everything runs nice and smooth. It seems like on my system the drivers don't really accelerate anything until they're forced to.
I might not have installed XGL before fglrx, I don't remember now.

Thanks for the help, I'm going to have to reinstall now anyway, dumping my RAID array, as making fake RAID work with dual booting is just too difficult for my first experience with Kubuntu.

---

