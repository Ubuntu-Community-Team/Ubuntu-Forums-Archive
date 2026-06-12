---
title: "Totem plays DVDs, just not the right way"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by TRANQU111TY on 2008-01-26
First of all when I insert a movie this message comes up:

> Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.

That's fine. All I need to do in Totem is go to the menu "'**Movie**' -> '**1. cdrom0**'" and the movie will start playing. The only problem is I can't click '**Next Chapter/Movie**' to move onto the next scene. The whole movie just seems to be one file and I have to seek manually to find the next chapter. Any suggestions?

Second, and I'm not colour blind, the colours are messed up, the lips are green and sky is white etc... Help please :)

---

### Post by TRANQU111TY on 2008-01-26
Fixed the colour issue :) [http://ubuntuforums.org/showpost.php?p=4120806&postcount=7](http://ubuntuforums.org/showpost.php?p=4120806&postcount=7)

---

### Post by RomeReactor on 2008-01-26
Hi. Totem-Gstreamer currently doesn't handle DVD menus; try switching it to Xine:
```
sudo aptitude install totem-xine libxine1 libxine1-ffmpeg libxine1-gnome libxine1-plugins
```

---

### Post by TRANQU111TY on 2008-01-28
> **RomeReactor said:**
> Hi. Totem-Gstreamer currently doesn't handle DVD menus; try switching it to Xine:
```
sudo aptitude install totem-xine libxine1 libxine1-ffmpeg libxine1-gnome libxine1-plugins
```

Thank you so much! The picture is clearer as well :)

I just don't get why they don't include it with the default Gutsy install (legal issues?). It's just far better! There isn't a downside is there?

---

### Post by RomeReactor on 2008-01-28
> **TRANQU111TY said:**
> Thank you so much! The picture is clearer as well :)

I just don't get why they don't include it with the default Gutsy install (legal issues?). It's just far better! There isn't a downside is there?

Performance-wise there's no downside; however, the Xine codecs are not installed by default due to [some licensing and patent issues]("https://help.ubuntu.com/7.10/musicvideophotos/C/codecs.html"). Gstreamer is more modular than Xine, so it allows you to install only those libraries that you need or want; Xine is more monolithic, in that it's mostly just about libxine1 and libxine1-ffmpeg, and it's a case of all or nothing.

---

### Post by Paul86fxr on 2008-02-24
I've installed what i thought was every codec possible and still can play anything, keeps giving me the encripted message.   and new ideas?

---

