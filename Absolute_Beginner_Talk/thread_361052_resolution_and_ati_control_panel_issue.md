---
title: "resolution and ati control panel issue"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by gamerzl on 2007-02-13
what would be the best resolution for my screen, and how would i set it because the gui settings don't let me change anything even within administrator mode

i'm running an ati x1600, with a 15.4 inch widescreen lcd laptop display

(and how would i change it to work) ati's drivers have already been downloaded

and the ATI control in the kmenu doesn't go anywhere, according to it it is suppost to run fireglcontrolpanel
but nothing appears, how can i fix this

---

### Post by nereid on 2007-02-14
You change the resolution via the Display in the Settings menu. The easiest way to explain how to change the resolution is this:

Open a terminal, type in "gksudo gedit /etc/X11/xorg.conf" and search for the following

```

Section "Screen"
    // here comes some more things, the following should be at the bottom of this section

    SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "400x300" "320x240"
    EndSubSection
EndSection

```

In the Modes line are all available resolutions. If you want to add one, just write it in there (the one at the front will be tried first, if it works this will be your resolution, if not, X will try the second entry, and so on).

Hope I could help you.

---

