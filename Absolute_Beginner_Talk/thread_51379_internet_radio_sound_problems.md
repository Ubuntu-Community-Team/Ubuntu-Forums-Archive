---
title: "internet radio sound problems"
date: 2005-07-23
forum: Absolute Beginner Talk
---

### Post by TennCyclist on 2005-07-23
Extreme newbie here.  When trying to listen to internet radio via streamtuner, shoutcast, live 365, etc. with beep media player and xmms I'm not getting any sound.  No problems with the couple of default stations available on rythmbox, also no problems when playing a cd.  Both beep mp and xmms indicate  a connection on interface but nary a peep from my speakers.  Any guidance on this would be greatly appreciated.  Thanks.

---

### Post by adwait on 2005-07-23
Umm.....maybe the stations you are trying to listen require some special codecs or something? Could you be more specific? Which stations?

---

### Post by TennCyclist on 2005-07-24
Thanks for answering but I've got it figured out now.  Had to change the output plugin on both players to esd.  works great now plus no hang ups.

---

### Post by varunus on 2005-07-24
TennCyclist, you may also want to look into the following howto so that ESD and ALSA can play sounds at once:

[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

I would change one thing from the howto, though, some ppl have reported lag in sound if they use the howto word for word.

In the /etc/asound.conf, use the following settings instead:

```

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 8192
rate 48000
}
bindings {
0 0
1 1
}
}

```

Good luck.

---

### Post by TennCyclist on 2005-07-25
I followed the directions, streaming radio via xmms player sounds great as does cd player, but my gnome background sounds, logon music, etc. had alot of what sounded like static so I changed the /etc/asound.conf back to the settings in the original post and it seems to have cured the static problem.  Is their any changes to your settings that would get rid of the static in the background sounds?

---

### Post by varunus on 2005-07-25
Some people have reported that changing their esd.conf section that say "-d default" to say "-d dmixer" fixes the static problem.  Try it out.

Good luck.

---

### Post by TennCyclist on 2005-07-25
Redid all the settings again with your suggestions.  It took care of the static in the Gnome desktop sounds.  Had a little bit when playing radio streams though with xmms and beep mp.  Changed multimedia systems settings back to esd and player prefs back to esd, seems to have cleared the static up.  Sound is alot clearer.  What benefits am I losing by having my settings on esd.  Newbie here trying to understand reasons behind actions.   

By the way, thanks a million for helping me out. :-)

---

### Post by varunus on 2005-07-26
A quick primer on sound:

ALSA is the Advanced Linux Sound Architecture.  It is the way that the kernel sees your sound cards, and output that goes to ALSA goes directly to your sound card (generally).  However, on some cards, ALSA has problems because once a program accesses the sound card, everything else is blocked from access.

ESD is the Enlightenment Sound Daemon.  This is a program that can accept sound from multiple sources, merge them, and play them back to the sound card (so ALSA sees only one sound coming from ESD).

What you have done in the configuration that you just went through is set up something called the DMIX plugin, which lets ALSA handle having multiple programs access the sound card.  (It does something similar to ESD.)  ESD usually has some lag associated with sound played through it, however; ALSA's dmix plugin does not have very much lag, usually.  (However, the settings in the howto produced lag from what I've seen; mine don't produce lag, but can make scratchy sound on some cards.)

One thing to look at:  How high do you have your volume set?  The current version of ALSA can sometimes make scratchy sound if the volume is above 80%.  Set it to about 75%, change your outputs back to ALSA, and see if you still have problems.  I recommend you use ALSA's lag-free sound (since you're accessing your sound card directly) instead of going through ESD (an extra layer, causing lag).

---

