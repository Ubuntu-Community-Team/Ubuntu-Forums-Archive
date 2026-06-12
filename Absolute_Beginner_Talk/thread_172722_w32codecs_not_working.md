---
title: "w32codecs not working"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by kart3r on 2006-05-09
i've installed w32codecs on my computer.I'm running Ubuntu Dapper beta on a AMD 1300Mhz and i still can't view movies :S help me please.I'm new with linux

---

### Post by louis_nichols on 2006-05-09
Well... i don't know what the issue might be with the w32 codecs, but here is the way I watch movies and haven't had any issues for the most part.

Just install totem-xine. :) It works and is simpler, even. If you're using dapper, you'd also have to install libxine-extracodecs.

Other options would be vlc or mplayer, which come with all codecs included, too, but I find them hard to use, either because of subtitles not in sync, or sound difficulties...

---

### Post by louis_nichols on 2006-05-09
ooops... double post. sorry

---

### Post by Hallavej on 2006-05-09
A bit more info please. What did you do and what are you trying watch with what player?.
You should have the codecs in /usr/lib/win32
If its a wmv file make sure that it is not DRM protected.
Try to use mplayer, it plays almost anything.

---

### Post by kart3r on 2006-05-09
where i can get mplayer?

---

### Post by mostwanted on 2006-05-09
[QUOTE=kart3r]where i can get mplayer?[/QUOTE]

You can install it with Synaptic. It's not in the main repository, so you'll have to enable the rest of the repositories (I think it's in Universe):

[http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories)

---

### Post by Sef on 2006-05-09
> i still can't view movies

From Restricted Formats:

> Note: WMV files encoded with DRM (Digital Rights Management) are not playable by the codecs.

So are they WMV with DRM?

---

### Post by kart3r on 2006-05-09
Sef sorry but my connection went down.I can now see movies, I forgot to add some repositories.Sorry :s thks for your help m8s

---

