---
title: "Dell front buttons"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Devile on 2006-09-10
I have a 6400 inspiron and there ar ebuttons on the front of the machine for audio control...  the volume controls work with amarok however the stop/play/next/back buttons odn't do anything, i sthere anwyasy to make them work?

---

### Post by slibuntu on 2006-09-10
Ok i'm going to bump this cos id like an answer too

---

### Post by Frostmourne on 2006-09-10
If you are using GNOME, go to Preferences > Keyboard Shortcuts, find the appropiate command, and press the media button you want to assign it to. That's all I had to do with my Inspiron E1505 which I think is almost the same as the 6400.

---

### Post by David Corrales on 2006-09-10
> **Frostmourne said:**
> If you are using GNOME, go to Preferences > Keyboard Shortcuts, find the appropiate command, and press the media button you want to assign it to. That's all I had to do with my Inspiron E1505 which I think is almost the same as the 6400.

I did the same thing and my Inspiron 9300 works perfectly.

---

### Post by jordanmthomas on 2006-09-10
On my i6000 I had to choose Microsoft Wireless for some reason...

---

### Post by Devile on 2006-09-10
perfect thanks guys

---

### Post by macpointman on 2007-05-04
Worked like a charm on my Dell Inspiron E1505.  Though you have to make sure that you select the 0xa2 entry (press the Play/Pause button until you see that entry) for the Play  (or play / pause) button and leave the Pause entry disabled.  One button controls both functions.  Works like a charm for me.

Linux ROCKS


MacPointMan

---

### Post by BrowneR on 2007-05-18
this was working fine for me under edgy.

i just upgraded to feisty and now only the volume buttons on my 9300 work, the playback controls are inactive.

when i press the respective keys in the gnome keyboard shortcuts dialog the corresponding hex values appear in the fields and will work for applications such as totem.

however amarok doesnt recognise the keys in its shortcuts dialog and fails to use them. as it uses the kde libraries i can understand it ignoring the gnome keyboard shortcuts however in the past it would at least let me set up shortcuts in amarok itself. any ideas people?

---

### Post by BrowneR on 2007-06-22
I have written an Amarok script to allow the use of multimedia keys in fiesty (and other gnome 2.18 distros).

There is no fuss at all - just load the script into amarok's script manager and configure the keys in
system-->preferences-->keyboard shortcuts

done.

get it here [http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910](http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910)
or install it directly from the Amarok script manager - its called "gnome multimedia keys".

this should be the fastest way to get it working.

any problems just send me a pm.

hope this helps. would love your feedback and bug reports.

---

### Post by rouge568 on 2007-07-23
What about for video? I want to use them for dvds on mplayer. Is there a way to do it so that by default it is for sound and only when I open mplayer/gxine/etc. it switches to video commands? Thanks in advance.

---

### Post by BrowneR on 2007-07-23
i dont think there is an easy solution to that problem. its really up to the individual applications such as mplayer/vlc/xine etc to support hotkeys.

you might try investigating the ['hotkeys']("http://sourceforge.net/projects/hotkeys") [package]("http://packages.ubuntu.com/edgy/x11/hotkeys") as it may allow you to do what you require although i have never used it and so cannot help you there. i think it provides an way of configuring key actions to suit your needs via xml config files. good luck.

---

### Post by gottferdamnt on 2007-07-28
Please, help me to do the same on XFCE for AmaroK. Otherwise tell me how is called the keyboard manager of gnome to install it (without install all gnome packages). thanks !

---

### Post by BrowneR on 2007-07-29
i think this is what your after:
```

gnome-keybinding-properties

```

---

### Post by gottferdamnt on 2007-08-04
I found a better way ! XFCE allows to change the keyboard layout, choose Dell Inspiron 6xxx/8xxx as Default model instead of xorg default layout. So you could use the front boutons with amarok (just modifying global shortcuts). 

BrowneR thank though !

---

