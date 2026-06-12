---
title: "Totem doesn't play sound"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-03-29
I have installed codecs to play avi files, but totem doesn't seem doesn't seem to play them properly. It plays the video but not the audio. However, I am trying VLC and it played the file fine. Can someone tell me how to fix this?

Also where, can I get more codecs ?

---

### Post by crispy_420 on 2007-03-29
totem-xine?

---

### Post by kittyhawk63 on 2007-03-29
You probably have Totem gstream loaded by default.  Go into Synaptic and install Totem Xine. It will automatically remove Totem gstream. Hope that will help.

---

### Post by noorez on 2007-03-29
I already have the totem-xine package installed.

---

### Post by kittyhawk63 on 2007-03-29
> **noorez said:**
> I already have the totem-xine package installed.

I'm sorry that is all I can tell you. It solved my problem. Keep posting. Someone should be able to help. 
kh

---

### Post by crispy_420 on 2007-03-29
What format is the audio portion of you movie?

---

### Post by cowlip on 2007-03-29
It may be a problem with ESD ALSA or OSS.  Try going into System->Preferences->Sound and choosing different sound server options.  Different ones may work on your sound card.

Also, if you have two sound cards in your system (Eg., soundblaster live plus an intregrated chip on your motherboard), pick the one in that sound applet which your speakers are connected to.

In earlier versions of Gnome, some Gnome apps were hardcoded for ESD but I think that's changed now.

---

### Post by Hutom on 2007-03-30
I can't play vcd in totem. I have tried both totem - xine and totem - gstream. None of them worked. By the way, vlc player too did not work. What went wrong?

---

### Post by Hutom on 2007-03-30
When I try to play vcd in totem, it says, "there is no input plugin to handle the location of this movie". What to do?

---

