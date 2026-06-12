---
title: "Cut down install"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by Druidor on 2006-09-13
This may sound like a half arsed thought.

I want to install Ubuntu onto a machine with the gnome desk but without all of the additional applications installed

office
gimp
games
etc..

All I require is a GUI desktop with Java & Azureus keeping as much disk space as possible without compromising the whole feel of Ubuntu.

Would the server install & an sudo apt-get install ubuntu-desktop do this or does the desktop command install all of the paraphanalia that I do not require.

It is being used on a PIII 450MHz machine with limited memory

---

### Post by croak77 on 2006-09-13
Do a server but install x-window-system-core xserver-xorg gnome-core gdm and then any other apps you want. ubuntu-desktop is the default packages on the cd.

---

### Post by Druidor on 2006-09-13
Many thanks for the info will give it a try on my soon to be defunct XP machine

---

