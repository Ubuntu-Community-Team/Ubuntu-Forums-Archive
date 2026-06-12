---
title: "need help with flash video"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by newbuntumom on 2007-12-28
I successfully installed Edubuntu 7.10 for my 6-year-old, and most everything is working fine.  Now he wants to watch beginner guitar videos at [http://www.littlekidsrock.tv/](http://www.littlekidsrock.tv/).  Firefox said I needed a plug-in so we installed Gnash and tested it with some other flash movies.  It worked fine with those, but not with [http://www.littlekidsrock.tv/](http://www.littlekidsrock.tv/).  I was wondering if someone smarter than I would be so kind as to look at that site and be able to tell what exact plug-in, revision, etc. I needed?  Pretty please?  The 6-year-old is beginning to gripe that maybe we should just get Windows "like everyone else."

Also, if I do get another plug-in, how do I make Firefox choose between one or the other?  I think there's an add-on that does that but for Windows only?

---

### Post by Perfect Storm on 2007-12-28
Gnash is not perfect yet, in the meantime you can use flash instead. Uninstall gnash then;

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo aptitude install flashplugin-nonfree
```

Now flash is installed.

---

### Post by billgoldberg on 2007-12-28
Yeah, gnash isn't without flaws.

Just google for flash player and download the linux one. It should install itself and ask you what browsers to install itself for.

---

### Post by newbuntumom on 2007-12-30
I installed the newest flash 9, and for some reason, it would not work at all for me.  I mean, I wouldn't see the puzzle piece thing that means the plug-in was altogether not installed; instead, the flash area would just be totally blank.  After reading some more about it I decided to try 9r48, which worked fine.

---

### Post by Perfect Storm on 2007-12-30
Yep, there's a "bug" in the flash package. Adobe have change some stuff which breaks it.

---

### Post by esva on 2007-12-30
I read in  another thread that using opera 9.50 you could use flash, I checked the site you mentioned and I could see it with this browser . I downloaded it from the site, download the 9.50 version, not the 9.25 cause you can't see any flash in that one.

---

