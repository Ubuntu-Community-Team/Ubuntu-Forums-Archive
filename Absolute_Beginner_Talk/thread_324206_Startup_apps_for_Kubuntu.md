---
title: "Startup apps for Kubuntu"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by drito on 2006-12-23
How to add startups for KDE session? I have done it for GNOME, but applications are not starting in KDE by default. I have both GNOME and KDE installed.

---

### Post by mjm115 on 2006-12-23
In your home folder,  there is a hidden folder '.kde/Autostart'.  Place links to your applications in this folder.

~/.kde/Autostart

---

### Post by Frak on 2006-12-23
Or go to system settings and and sessions, and then startup apps.

---

### Post by drito on 2006-12-23
Thank you both. However, I was able to use only mjm115's tip. I am not able to find anything like ***add startups*** in system settings/manage sessions.

---

### Post by Frak on 2006-12-23
Since I'm not in Kubuntu right now I can remeber where its at, but somewhere in system settings.

---

### Post by zencoder on 2007-01-15
Yeah, no joy for me either, **Frak**.  I used the search bar in System Settings and the only two sections that had "Startup" were 'Splash Screen' and 'Sound System', and neither one had anything to do with startup scripts.  Was this perhaps removed/hidden in the latest release?

FWIW, Kubuntu 6.10 with all patches/updates, no extra or additional software installed yet (except the VMWare-Tools package, since this is a VM guest OS.)

---

### Post by Frak on 2007-01-15
I know this is off subject, but **zencoder**, have you tried Qemu? (or better yet, use [QemuManager]("http://www.davereyn.co.uk/download.htm") for a GUI frontend), just saying, because Qemu is
1. free
2. Fast! (near native host speed)
3. also a processor emulator, able to emulate 64-bit processors also, PPC is a little rough, thats where [PearPC]("http://pearpc.sourceforge.net/downloads.html") comes in.

EDIT
Sorry forgot, it also emulates MIPS, Sparc, and ARM architectures.

---

### Post by NZ-Wanderer on 2007-01-16
Even tho we do have a Session Manager under "system Settings/Advanced/" I cannot figure out any way to edit it at all...
Looks like Kubuntiu doesn't have any way of adding or editing startup stuff 

> **zencoder said:**
> Yeah, no joy for me either, **Frak**.  I used the search bar in System Settings and the only two sections that had "Startup" were 'Splash Screen' and 'Sound System', and neither one had anything to do with startup scripts.  Was this perhaps removed/hidden in the latest release?

---

