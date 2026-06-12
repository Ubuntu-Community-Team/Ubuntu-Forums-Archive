---
title: "XMMS stops playing"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-04-05
I just installed XMMS, along with gstreamer-mad0.8 and everything needed to play mp3s. However, from time to time, when switching to the next song in playlist, XMMS pops out a dialog box telling me that it cannot use the soundcard: either it is not properly configured or the audio card is used by other application. However, after selecting some other songs in playlist (or even the same song for a couple of times) and getting the same message, everything returns to normal. But doing this is annoying. I just want to fill a playlist and continuously play the songs, I don't want to watch XMMS and hunt for the popup.

What can I do?

---

### Post by Qrk on 2006-04-05
Xmms defaults to using the OSS sound plugin, which is tempermental at best. I'd switch to using ALSA, which you can do under

Options->Preferences->I/O plugins, select ALSA on the drop down menu.

---

### Post by Gracye on 2006-04-05
this happens to me too! I posted a thread about it earlier but no one has responded.

anyone know how we can stop this?

---

### Post by zugu on 2006-04-05
Thank you for the info.

---

