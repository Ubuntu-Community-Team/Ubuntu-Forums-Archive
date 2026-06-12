---
title: "Magnifier-cut 1.3 - Screen magnifier for Ubuntu / Linux (i386)"
date: 2012-09-01
forum: Assistive Technology &amp; Accessibility
---

### Post by rodrigo.miguel on 2012-09-01
Hello,

I want to share the release of version 1.3 of Magnifier-cut...

The Magnifier-cut is a recompilation of the gnome-mag, is an "adaptation", which aimed to meet specific accessibility of two users with visual impairment, to whom I support.

The main feature of Magnifier-cut is the size of the magnifier, which occupies only 18.75% of the vertical resolution of the monitor.

It is compatible with Unity, Gnome, KDE, Xfce, LXDE, etc.

Requires gnome-mag installed on your system.

For more information and download, please visit: [http://linuxlike.blogspot.com.br/2010/12/magnifier-cut-ampliador-de-tela-baseado.html](http://linuxlike.blogspot.com.br/2010/12/magnifier-cut-ampliador-de-tela-baseado.html)

Other information: [http://linuxlike.blogspot.com.br/search/label/Magnifier-cut](http://linuxlike.blogspot.com.br/search/label/Magnifier-cut)

Demo Video: [http://youtu.be/hQdoN_JFQ88](http://youtu.be/hQdoN_JFQ88)

***

BEFORE INSTALLING

Requires gnome-mag:

sudo apt-get install gnome-mag


INSTALL

Extract magnifier-cut_1.x.tar.gz ...

chmod +x *.sh
./instalar.sh


INSTRUCTIONS

Magnifier bottom (or command magnifier-cut-bottom): ideal for Unity. Works best in Unity-2D.

Magnifier bottom indented (or command magnifier-cut-indented): specially designed for use with GNOME 2 / GNOME Classic (no effect).

Magnifier bottom overlap (or command magnifier-cut-overlap): for use in GNOME 2 / GNOME Classic (no effect). It should not be used with the desktop effects enabled (Compiz / Metacity compositing) - the interface is unusable (as a solution, press Alt + SysRq (or PrtScr) + k to end the interface and restart the system).

Magnifier top (or command magnifier-cut-top): unlike the previous one, should only be used in GNOME, with effect from the Desktop enabled. It works quite well in Unity. Ideal for KDE and LXDE.

By default, the Magnifier magnification factor-cut is set to 5 (5x zoom). If you want to modify it, run (as administrator) command magnifier-cut-zoomfactor. So you can adapt the amplifier to your needs :)

The above commands and shortcuts execute scripts which in turn execute the binary magcut-indented or magcut-standard. Both magcut-indented as magcut-standard modifications are magnifier (gnome-mag). If you want to run Magnifier-cut with other parameters than those of scripts, can be based on manual own gnome-mag (man magnifier). However, some options magnifier, such as full screen mode (-f), will behave differently in Magnifier-cut.


SWITCH MAGNIFIERS

You can switch directly between the magnifiers (for example, between the top and bottom).


TO CLOSE MAGNIFIER

To close the Magnifier-cut, you can:

1. Clicking the shortcut magnifier running (or run the same command);
2. Use the shortcut "Close magnifier";
3. Run the command: killall -r magcu*


SETTING THE FACTOR OF MAGNIFICATION

As root:

magnifier-cut-zoomfactor

To restore the default:

sudo echo 5 > /usr/share/magcut/zoomfactor


UNINSTALL

./desinstalar.sh

---

### Post by abuismail on 2013-05-15
Thanks,
The magcut is very helpfull for me.
Can i get the 64-bit version ? 
One more thing, is there any way to set the magcut to follow the keyboard focus ?

Thanks

---

