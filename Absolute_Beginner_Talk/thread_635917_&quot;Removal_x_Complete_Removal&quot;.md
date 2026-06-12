---
title: "&quot;Removal x Complete Removal&quot;"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by IeU on 2007-12-09
Hi all,

i am trying to uninstall apps and other things i dont use.

as a linux newbie, first i tryed the "add/remove app", but on 95% of the cases it pops me with an error, saying "blablabla use synaptic"

so i launched Synaptic and i would like to for example uninstall the gnome bittorrent app and for example the default package manager ( unpack zip/rars, i plan to install 7zip )

so what is the big diff btw removal and complete removal ?

is it safe to use the complete removal as a newbie linux user ?

at the bittorent case,
it pops me another window saying it also saying
"to be removed"
*gnome bt download ( ok i want that uninstalled )
*unbuntu-desktop ( ah ? what is this, i dont want to uninstall my gnome desktop )

need some instructions and help, thanks a lot.

---

### Post by overdrank on 2007-12-09
> **IeU said:**
> Hi all,

i am trying to uninstall apps and other things i dont use.

as a linux newbie, first i tryed the "add/remove app", but on 95% of the cases it pops me with an error, saying "blablabla use synaptic"

so i launched Synaptic and i would like to for example uninstall the gnome bittorrent app and for example the default package manager ( unpack zip/rars, i plan to install 7zip )

so what is the big diff btw removal and complete removal ?

is it safe to use the complete removal as a newbie linux user ?

at the bittorent case,
it pops me another window saying it also saying
"to be removed"
*gnome bt download ( ok i want that uninstalled )
*unbuntu-desktop ( ah ? what is this, i dont want to uninstall my gnome desktop )

need some instructions and help, thanks a lot.

Hi and this link may explain some
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by Ub1476 on 2007-12-09
The reason it asks you to use Synaptic for certain apps, is because you remove something which is part of the default Ubuntu-desktop. So, everything which came preinstalled with the system, you'll have to remove through Synaptic, everything you installed yourself, you can remove from add/remove.

---

### Post by IeU on 2007-12-09
> **Ub1476 said:**
> The reason it asks you to use Synaptic for certain apps, is because you remove something which is part of the default Ubuntu-desktop. So, everything which came preinstalled with the system, you'll have to remove through Synaptic, everything you installed yourself, you can remove from add/remove.

o nice expl. thanks a lot :)

thanks too overdrank

---

### Post by staticvoid on 2007-12-09
complete removal removes config files and personal settings formthe home folde (hit ctrl H and you'll see them)

removal just deletes the program.

if it wants you to remove ubuntu-desktop, that shold be ok to do. i had it explained to me before but now I forget.. its like, you can install this package ubuntu-desktop and it gets all these apps that come with the dekstop, after that its safe to remove the retriever.

hope that helps even more :D


have fun with ubuntu!!! be sure to check out other distros to though ;) or different windows managers and stuff.

kubuntu, openbox, icewm, KDE, etc...

cya,

static

---

### Post by Nekiruhs on 2007-12-09
ubuntu-desktop is whats called a "metapackage". It has no applications in it by itself, but rather depends (requires installation of) a large set of real pacakges. This allows you to easily install a full desktop environment at once. For example installing kubuntu-desktop installs KDE. Uninstalling ubuntu-desktop won't matter now, but it may make upgrading to Hardy (8.04) a bit harder (Eg. reinstall ubuntu-desktop, upgrade, remove ubuntu-desktop).

---

