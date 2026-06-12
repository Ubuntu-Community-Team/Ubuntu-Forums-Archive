---
title: "Make &quot;volume UP/Down&quot; &amp; &quot;mute&quot; keys work"
date: 2007-05-30
forum: Apple Intel Users
---

### Post by Ubivetz on 2007-05-30
Hi All!

How to make these keys work? I have KMilo running (I'm using KDE) and when I press any of these buttons, I see dialog with progress bar, which is similar to Mac OS X one,
But sound volume has  not been changed!

---

### Post by benanzo on 2007-05-30
I believe that you simply need to change which ALSA channel is affected by the keyboard shortcut volume keys.  You can change which volume meter is affected by going to
(disregard these instructions, I just realized you're in KDE.  These are GNOME-specific, but you should have something similar. -- me=not a KDE user)
**System -> Preferences -> Sound**

and changing the default track at the bottom of the first tab under **Default Mixer Tracks**

On my first-gen MacBook with Intel Core Duo I have set the keyboard to control the **PCM** channel.  I have then set the **Front** and **Master** channel volumes to highest and control the overall system volume (speakers & headphones) with the **PCM** channel.

---

### Post by cevans on 2007-05-30
My guess is that right clicking on the mixer applet will probably get you to the settings you need to change.

---

### Post by Ubivetz on 2007-05-30
> **cevans said:**
> My guess is that right clicking on the mixer applet will probably get you to the settings you need to change.
Thanks, it works.

P.S.
I have assigned the rest button (CD eject) to /usr/bin/eject via xbindkeys-config.

---

