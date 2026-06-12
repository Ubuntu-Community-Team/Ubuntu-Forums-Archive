---
title: "beryl won't activate, metacity overrides"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by SaltyTaro on 2007-01-05
video drivers installed great, beryl installed great, xorg.conf changed the way it's supposed to be changed.  i go to the console and say "beryl-manager", and sure enough, it opens up.  but it doesn't work.  if i click on the dropdown menu and go to "Select Window Manager", and select "Beryl", instead of "Metacity", my windows start flashing a bit, and then it gets set back to Metacity.  i even tried turning off every option for beryl, but it still does this.  any suggestions?

---

### Post by mahiyar on 2007-01-05
This could be because beryl fails to initialize. Open a terminal, type "beryl" and see the error messages, if it is saying something about no composite, then add the following lines in your xorg.conf files, if its already not there.
 
Section "Extensions"
Option "Composite" "Enable"
EndSection

---

### Post by SaltyTaro on 2007-01-05
i get this when i put in "beryl" into the terminal
```
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```
nvidia?  i have an ati, is that what's going wrong?

---

### Post by mahiyar on 2007-01-05
What version of Ubunti are u using ist it 6.05 or 6.10.

---

### Post by eggdeng on 2007-01-05
You need to install the ATI proprietary drivers. See for example the guide at 
[http://ubuntuguide.org/wiki/](http://ubuntuguide.org/wiki/).

---

### Post by Sasa_Ivanovic on 2007-01-05
i had the same problem. Here's how i solved it :
i uninstall the beryl manager, and emerald themes :
```

sudo apt-get remove --purge beryl emerald-themes

```
then i restarted, then i installed them
```

sudo apt-get install beryl emerald-themes

```
there's also a wiki tutorial for installing beryl on Ubuntu, you might want to look this up!

---

### Post by SaltyTaro on 2007-01-05
- i tried turning composites enabled, and when i got back on i had all sorts of random problems.  windows would not have the tops, they'd sit over the top menu, and i couldn't switch between workspaces

- i'm running 6.10

- eggdeng, that wiki that you gave has a guide for beryl, which says "if glxinfo shows direct rendering: yes , then you are good to go".  i don't have a propietary driver installed, but i do have direct rendering on.  is that not good enough?

- just uninstall it and install it again?  i've installed it once using the wiki link above, and once using the guide on this forum (from the ubuntu document storage facility), and i've tried a mixture of the suggestions the two guides give, but i keep running into problems, like problems starting a session with xgl, or my comp just not doing anything

give me some time to install the propietary drivers (i've tried before, ended up settling for fglrx because it didn't kill my computer), and then i'll post in this thread again about how it went.  thanks for your guys' suggestions

---

