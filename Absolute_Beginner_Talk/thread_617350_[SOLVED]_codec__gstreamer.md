---
title: "[SOLVED] codec / gstreamer"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by teh'p3nsi0n3r on 2007-11-19
i dont know if this is a simple question or not? but last night i was watching some movies mpgs, and avi files, the codecs im using are the gstreamer ones from the reposortries.
After a while going to watch another movie they are still playing but in black and white and the sound is also fine, but i couldnt make sense of why all files are playing in black and white, i thought it might be a compiz-fusion issue so i disable all desktop effects and restarted...not the issue, still the same problem.
I removed the gstreamer codecs, restarted, movies wouldnt play....as they should becuase the codecs are removed, reinstalled gstreamer codecs and still the same issue in black and white.
the only thing i can think of is installed another movie codec to get .rm files to play in totem, there was a guide on an ubuntu wiki somewhere instead of install realplayer and this hasnt effected anything, but i dont know if this could be causing the issue or not?.

EDIT (the codec to the .rm files to play were installed ages ago and haent affected the gstreamer ones, this is only a recent issue but like i said i dont know if this is causing the issue).
Any help would be apreciated.

Thanks.

---

### Post by teh'p3nsi0n3r on 2007-11-19
the players used to test are VLC and Totem. so its not a player issue as far as im aware.

---

### Post by teh'p3nsi0n3r on 2007-11-19
bump, anyone?

---

### Post by teh'p3nsi0n3r on 2007-11-19
anyone?

---

### Post by mivo on 2007-11-19
Does this still happen after a reboot? I know rebooting isn't the Linux Way, but sometimes it still fixes stuff. ;) In Gnome I usually use the Xine-version of Totem and never had any problems with it. If nothing else helps, this might be worth a try. (The package is totem-xine.)

---

### Post by teh'p3nsi0n3r on 2007-11-19
hi Mivo, i installed the totem-xine player, and it removed the gstreamer one, and i checked the "about menu" its def using the xine lib, but still no joy, yea i tried rebooting still no joy, even removed the gstreamer plugins, and rebooted, still no joy, thing is VLC like i said still gives out the same issue.
On a side note before i done of that, i did go and play one of the original movie files that were black and white and they played in colour but after rebooting, went back to black and white. its really puzzling me, i tried all the above with compiz-fusion off btw.

any help apreciated, i really dont know whats going on.

---

### Post by teh'p3nsi0n3r on 2007-11-19
ok so ive removed totem all together, now mplayer and vlc are playing in colour, no gstreamer plugins, wtf!? lol :confused::)

---

### Post by mivo on 2007-11-19
Okay, so it's not the engine. Hmm, truly strange. I watch most of my movies in Xine-driven players (Totem in Gnome and Kaffeine in KDE), in different formats and encodings, and I never had the problem. Video drivers would be my next guess -- what are you using?

The puzzling part is that it's sometimes fine for you and sometimes not. I found something about the b/w problem [here]("http://www.xinehq.de/index.php/faq#CONTRASTBRIGHTNESSSATURATION"), but that doesn't seem relevant to your trouble.

Edit: Oh, so it is fixed? Maybe some kind of conflict?

---

### Post by teh'p3nsi0n3r on 2007-11-19
seems like it was a conflict, i reinstalled the totem-xine player and it was in black and white again but mplayer and vlc were fine with colour, the grstreamer plugins are removed i only put back the gstreamer extras for mp3s etc.
I went into the totem-xine prefs, and went to Video and reset defaults and the colour came back on. strange, very strange but seems like its solved. thanks for your help mivo :):KS

---

