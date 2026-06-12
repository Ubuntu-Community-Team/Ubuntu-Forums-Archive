---
title: "[SOLVED] Two Monitors...same size....Ubuntu always has 1 out of wack"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Tdukes on 2007-11-01
I have a wierd problem here.

I have 2 widescreen monitors that are native 1440x900
I can set both of them at the 1440x900 but when I log off and back on, 1 monitor is always out of wack.  The viewing field is outside of the monitor so I have to scroll up with the mouse to find the panel bar.

any help would be much appreciated.  

Driver setup should be good as is

---

### Post by Inxsible on 2007-11-01
what GPU do you have ?

---

### Post by buntunub on 2007-11-01
:popcorn:

Use #nvidia-settings for nvidia card, or the ATi config utility for ATi cards.

---

### Post by Tdukes on 2007-11-01
I have a Nvidia Geforce7800

do I need to download the graphics driver from the nvidia.com?

just trying to figure out what exactly you mean when you say "Use #nvidia-settings"

---

### Post by neekz on 2007-11-01
It means enter that into your terminal, I have the same issue. I let gutsy gibbson do all the work about drivers and that command did open up the editor box. I am going to play around to see if works.

---

### Post by alwiap on 2007-11-01
i have a 7800 gt and although i'm using 1 monitor at the moment, i have configured a dual monitor setup using 2 different monitors, have you tried:

```
gksudo nvidia-settings

```

in console and adjusting the settings there?  i was able to use this GUI and configure without any problems.  good luck.

---

### Post by Inxsible on 2007-11-01
> **alwiap said:**
> i have a 7800 gt and although i'm using 1 monitor at the moment, i have configured a dual monitor setup using 2 different monitors, have you tried:

```
sudo nvidia-settings

```in console and adjusting the settings there?  i was able to use this GUI and configure without any problems.  good luck.

```
gksudo nvidia-settings
``` would be a better option.

---

### Post by neekz on 2007-11-01
To save your changes you have to save it to your X config file correct??? If so that can break everything? Should I back it up if so how??

---

### Post by alwiap on 2007-11-01
> **Inxsible said:**
> ```
gksudo nvidia-settings
``` would be a better option.

thanks for correcting!

---

### Post by Inxsible on 2007-11-01
> **neekz said:**
> To save your changes you have to save it to your X config file correct??? If so that can break everything? Should I back it up if so how??
Yes backups are always a good idea before doing something.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by Tdukes on 2007-11-01
I just did the gksudo nvidia-settings and it worked.  You guys rock, thanks for the help

Now I have to figure out why I cant drag an open window onto the next monitor......but my cursor will just drag right over

---

### Post by neekz on 2007-11-01
Thanks I just backed it up, going to try to get dual display to work with my CRT and tv set.

---

### Post by Inxsible on 2007-11-01
> **Tdukes said:**
> I just did the gksudo nvidia-settings and it worked.  You guys rock, thanks for the help

Now I have to figure out why I cant drag an open window onto the next monitor......but my cursor will just drag right over

hmm. Do you have TwinView enabled ?

---

### Post by Tdukes on 2007-11-01
> **Inxsible said:**
> hmm. Do you have TwinView enabled ?

I got it figured out....I had to select the xinerama box.

all is good now.  thanks again everyone

---

### Post by Inxsible on 2007-11-01
> **Tdukes said:**
> I got it figured out....I had to select the xinerama box.

all is good now.  thanks again everyone
Awesome !

Please mark your thread solved. :)

Thread tools --> Mark thread as solved.

---

