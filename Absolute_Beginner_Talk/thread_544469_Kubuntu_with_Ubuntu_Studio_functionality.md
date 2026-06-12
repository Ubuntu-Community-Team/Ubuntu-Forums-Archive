---
title: "Kubuntu with Ubuntu Studio functionality"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by CleverWilly on 2007-09-06
Hello!

Please, help me to figure out how to do it best:

I've got Kubuntu installed. I want to add to my current setup Ubuntu Studio drivers and programms. However, I don't want to switch to Gnome desktop. I have also downloaded Ub. Studio Live CD. 

So I need:
1. Upgrade my current Kubuntu setup with Ubuntu Studio functionality using Live CD without any Internet downloads.
2. Retain Kubuntu desktop without KDE vs Gnome conflicts if possible. (Dont even need Ub St themes and screens)

I would appreciate your help.


P.S.
I also wonder if it's possible to add some functionality of JackLab distro like default freeBob availability and WineAsio? Installation of such thing is currently beyond me.

---

### Post by angrykeyboarder on 2007-09-06
> **CleverWilly said:**
> Hello!

Please, help me to figure out how to do it best:

I've got Kubuntu installed. I want to add to my current setup Ubuntu Studio drivers and programms. However, I don't want to switch to Gnome desktop. I have also downloaded Ub. Studio Live CD. 

You don't have to switch to GNOME. Ubuntu Studio is just a collection of Multimedia apps that are already in the Ubuntu archives, plus a different GNOME theme (and system sounds).

If you install all of it, you'll have both GNOME and KDE. Once you get to your Logoin screen you can slect wihch you want to use.

I've got GNOME, KDE and XFCE in my Ubuntu install right now. I've also got most (but not all) of the Ubuntu Studio apps installed as well.

> **CleverWilly said:**
> So I need:
1. Upgrade my current Kubuntu setup with Ubuntu Studio functionality using Live CD without any Internet downloads.
2. Retain Kubuntu desktop without KDE vs Gnome conflicts if possible. (Dont even need Ub St themes and screens)
I would appreciate your help.

If you want to avoid re-downloading progams you already have on the CD just install them from the CD.

Open a terminal and use the "[apt-cdrom]("http://fts.ifac.cnr.it/cgi-bin/dwww?type=runman&location=apt-cdrom/8")" command. This will add the CD to your sources.list file. 

Then just install the UbuntuStudio metapakages (some or all of them).

They all begin with "ubuntustudio-".

(e..g. ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video)


> **CleverWilly said:**
> 
P.S.
I also wonder if it's possible to add some functionality of JackLab distro like default freeBob availability and WineAsio? Installation of such thing is currently beyond me.

That's beyond me too. :)

---

### Post by CleverWilly on 2007-09-07
Angrykeyboarder, thanks a lot! :)

---

