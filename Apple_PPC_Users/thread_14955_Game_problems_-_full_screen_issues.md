---
title: "Game problems - full screen issues"
date: 2005-02-10
forum: Apple PPC Users
---

### Post by dubdubdub on 2005-02-10
When I try to launch games that require full screen play (Tux Racer, KQ, etc.) the screen is very garbled, repeated and barely legible. 

How do I check if I have proper video drivers installed or is it possibly something else?

G3/500 iBook (1024x768). Color depth at 16 or 24 doesn't make a difference.

---

### Post by dubdubdub on 2005-02-14
All I want to do is play tuxracer! Can someone at least tell me where the options file is? According to the site I can edit it with Gedit and change it to windowed mode.

I figured out if I can get games to load in windowed mode they are fine (I accidentally changed KQ to windowed mode and it works now).

---

### Post by Laf on 2005-02-14
I think you should try to open you X configuration file.

It depends which server you are using :

[list=a]
[*]XFree86 : /etc/X11/XF86Config-4
[*]X.org : /etc/X11/xorg.conf
[/list]

Now you will have to search in the file a part like this :

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility 9000 M9+ (RV250)"
        Monitor         "COLOR LCD"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection

``` 

You see the "Modes" part ? Just remove all configurations which are not "1024x768" (the only configuration working with your LCD screen).

You should keep something like this at the end :

```

        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection

```

Yes of course you will have to change it for ALL the "Depth" parts...

After this, just restart X (CTRL+ALT+Backspace) at GDM login.

---

