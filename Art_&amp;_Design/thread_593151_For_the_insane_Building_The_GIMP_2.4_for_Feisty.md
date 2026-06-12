---
title: "For the insane: Building The GIMP 2.4 for Feisty"
date: 2007-10-26
forum: Art &amp; Design
---

### Post by DerangedDingo on 2007-10-26
[https://help.ubuntu.com/community/GIMP2.4-on-Feisty](https://help.ubuntu.com/community/GIMP2.4-on-Feisty)

I just wrote the wiki page after trying to do it myself.
I wrote down everything I remembered too, and I hope someone could actually compile it for Feisty and release it somewhere, maybe in a Launchpad PPA for the rest of us who want the 2.4 release but don't want to upgrade to Feisty

Have a look, and feel free to try it yourself or add information.
Opinions and critiques are welcome as well

Have at it!

---

### Post by cinematography on 2007-10-30
Thank you for this. I'm not quite ready to switch to Gusty yet, and this tutorial looks promising. And I'd also appreciate it if someone could make a Gimp 2.4 package for Feisty.

---

### Post by adamorjames on 2007-10-31
It's not in the backports? :confused:
Well, if not, great work!

---

### Post by Tsu Dho Nimh on 2007-10-31
I cheated.  I'm running Win2K on VMware. Downloaded the Windows Package and installed it.

If anyone gets a good Ubuntu binary of it, I'd like to know.

---

### Post by rax_m on 2007-11-01
There are debs for gimp 2.4 at getdeb.net ... 
they don't seem to be platform specific, but I haven't had the guts to uninstall my current gimp install and try it yet ;) 

Anyone else feeling braver?

---

### Post by Chris Johnson on 2007-11-05
I tried installing Gimp 2.4 from source a week or so ago. Installed GTK+ 2.10.14, and got the new version of Gimp running without too much trouble.

HOWEVER, for some reason installing GTK+ 2.10.14 reverted all of my GTK 2 window decorations to GTK 1 style: not just the style of Gimp, but the whole Gnome interface. I reverted to my old GTK with 'sudo make uninstall' in the GTK 2.10.14 source directory, and all was back to normal with (as one would expect) a non-functioning Gimp 2.4. 'sudo make uninstall' in the Gimp 2.4 source directory resurrected Gimp 2.2 though, so no harm done. No real success though.

---

