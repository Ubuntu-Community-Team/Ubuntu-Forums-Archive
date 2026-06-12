---
title: "[SOLVED] All videos play in black and white"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by ImThatNerd on 2008-03-15
All my videos play only in Black and White now and yesterday they were in color. In both VLC and the default movie player I went into the preferences and selected restore to defaults for the colors but that messes up the picture even more. Any help?

---

### Post by joshrobinson on 2008-03-15
```
sudo rm -r ~/.gconf/apps/totem
```

log out and log back in

should work for totem, not sure about vlc, give it a shot

---

### Post by ImThatNerd on 2008-03-15
> **joshrobinson said:**
> ```
sudo rm -r ~/.gconf/apps/totem
```

log out and log back in

should work for totem, not sure about vlc, give it a shot

Thanks it worked in vlc too.

---

### Post by joshrobinson on 2008-03-15
> **ImThatNerd said:**
> Thanks it worked in vlc too.

your welcome

---

### Post by SonicSteve on 2008-03-26
A client of mine had this issue and it solved the problem for Totem, VLC and Kaffeine.

Can someone explain this command to me so I understand what it does and why it works?

---

### Post by banjopikker on 2008-03-28
I had the same problem.  This solution fixed it right up. Thanks

---

### Post by lswest on 2008-03-28
the command removes the preferences folder of the program completely, so that the next time you start the app the whole folder is re-created, at default, which fixes it if some config files get messed up.

---

### Post by SonicSteve on 2008-03-28
> **lswest said:**
> the command removes the preferences folder of the program completely, so that the next time you start the app the whole folder is re-created, at default, which fixes it if some config files get messed up.

Thanks, so then why does VLC or Kaffeine care about Totem settings?

---

### Post by lswest on 2008-03-28
i tried to explain that in the PM i sent you, but most of the video settings used by other programs are based off what is in the totem configurations, so if you fix those, vlc and such work too.

---

### Post by SonicSteve on 2008-03-31
I'm sure at some level this makes sense. It still seems odd though since Kaffeine is a KDE program. Sounds like it's a Gnome sort of thing.

---

### Post by hooligan36 on 2008-04-23
Thanks. I had the black and white problem with Mplayer and that command fixed it!

---

### Post by banjopikker on 2008-04-28
Didn't work for me. I have the same problem . I ran the code in terminal and it returned .... unable to resolve host ubuntu. I am running 8.04.

---

