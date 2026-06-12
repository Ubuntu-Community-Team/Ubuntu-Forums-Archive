---
title: "Installing KDE after beryl"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2007-04-01
I'm interested in trying out KDE.
I have a nicely set up Feisty machine.
I also have nVidia Beryl.
Would it be dangerous to install KDE? and is:
> sudo aptitude install kubuntu-desktop
the right command? I just want KDE. Not to replace my bootloader or whatnot. Thanks :D

---

### Post by ajmorris on 2007-04-01
> **alex-desktop79 said:**
> I'm interested in trying out KDE.
I have a nicely set up Feisty machine.
I also have nVidia Beryl.
Would it be dangerous to install KDE? and is:

the right command? I just want KDE. Not to replace my bootloader or whatnot. Thanks :D

It is not dangerous. Installing that package is right but that will replace you bootloader and some document files such as firefox's so that when u open firefox it says kubuntu 7.04 feisty. If you do sudo apt-get install kde i believe that will not change you bootloader.

---

### Post by NikoC on 2007-04-01
I had KDE and Gnome running for a while just to try things out... no problems what so ever with beryl, it just replaces the window manager in both desktops. Installing KDE after Gnome and removing it again later on never had any effect on my bootloader.

---

### Post by ajmorris on 2007-04-01
> **NikoC said:**
> I had KDE and Gnome running for a while just to try things out... no problems what so ever with beryl, it just replaces the window manager in both desktops. Installing KDE after Gnome and removing it again later on never had any effect on my bootloader.

it doesn't usually replace the windows manager in gnome and kde. But i have always had kubuntu-desktop replace my bootloader.

---

### Post by alex-desktop79 on 2007-04-01
I did
> sudo apt-get install kde-core
Worked very nicely! Except all my gnome applications are fugly in KDE.
And this is the second time I try to post this, firefox crashed the first.

---

