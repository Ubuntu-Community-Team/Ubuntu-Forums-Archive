---
title: "Sound works sometime"
date: 2005-04-12
forum: Apple PPC Users
---

### Post by rantanplan on 2005-04-12
Hey all,

I am new to PPC arch and Ubuntu. I have the latest iBook G4, some people told me to use snd-powermpac module that I put in /etc/modules to load at boot. But when I try to play something with XMMS, it tells that I don't have sound card. I change the plugin from OSS to ALSA,it works !

At the next reboot, XMMS cannot play anything, I switch Alsa plugin into OSS, but there is nothing, then I try with eSound plugin, it works now, but I know at the next reboot XMMS won't play anything with eSound plugin.

( I don't use Rhythmbox because all radio stations that I tried, it doesn't work. I didn't
to play a mp3 with Rhythmbox yet.

Help me to fix that, thanks for any help.

---

### Post by farruinn on 2005-04-28
[QUOTE=rantanplan]Hey all,

I am new to PPC arch and Ubuntu. I have the latest iBook G4, some people told me to use snd-powermpac module that I put in /etc/modules to load at boot. But when I try to play something with XMMS, it tells that I don't have sound card. I change the plugin from OSS to ALSA,it works !

At the next reboot, XMMS cannot play anything, I switch Alsa plugin into OSS, but there is nothing, then I try with eSound plugin, it works now, but I know at the next reboot XMMS won't play anything with eSound plugin.

( I don't use Rhythmbox because all radio stations that I tried, it doesn't work. I didn't
to play a mp3 with Rhythmbox yet.

Help me to fix that, thanks for any help.[/QUOTE]
 This actually isn't a ppc specific issue, but Esound is the proper output plugin as it sends the sound to esd (the sound daemon used by Gnome).  Odd that XMMS didn't remember your settings over reboot though.

---

