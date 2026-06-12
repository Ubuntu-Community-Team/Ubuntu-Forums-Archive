---
title: "Windows Key + Num Lock with xubuntu"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2006-10-11
Does anyone know how to make the windows key on the keyboard do stuff? Also Does anyone know how to have num lock turned on at boot? i'm using xubuntu.

---

### Post by lowracer on 2006-11-09
For Edgy and GNOME at least, there's a good and easy to follow guide here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_turn_on_Num_Lock_on_GNOME_startup](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_turn_on_Num_Lock_on_GNOME_startup)

And to get that windows key to do useful work, here's something that might be of use:
[http://marc.abramowitz.info/archives/2006/06/22/getting-the-windows-key-to-work-in-gnomeubuntu/](http://marc.abramowitz.info/archives/2006/06/22/getting-the-windows-key-to-work-in-gnomeubuntu/)

I bet XFCE has something analogous.

---

### Post by kalikiana on 2006-11-09
As for the Windows or 'Super' key, either System->Window Manager is your friend if you want to bind it to a XFCE function or System->Keyboard will allow you to assign a command to it.

To have numlock activated by default, you may open the Autorun application of XFCE which is found in the System menu and add 'numlockx on' as a new command. If you don't have numlockx, just do a 'sudo aptitude install numlockx' before.

---

### Post by nyxynyx on 2006-12-09
Switching my num lock on doesnt allow me to input numbers from that side of the keyboard! And when i go to System> Keyboard> Keyboard Options i get a blank screen... Help!

---

### Post by pacas on 2007-02-16
I am running Xubuntu 6.10, alternate.  To activate NumLock on boot, Numlockx had to be installed and listed in the Autostarted Applications List in the Settings menu.

---

