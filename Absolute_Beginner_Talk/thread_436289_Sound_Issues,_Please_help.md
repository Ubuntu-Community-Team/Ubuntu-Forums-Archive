---
title: "Sound Issues, Please help"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by ~chinook~ on 2007-05-07
Sound works fine in avi and mp3 files etc Sound will not work in real media, youtube videos. Any ideas?

---

### Post by ~chinook~ on 2007-05-07
Not to get pissed off, but I have heard so much of the Ubuntu community and as of recently on my last three topics I have had little to no help

---

### Post by NeoLithium on 2007-05-07
Have you installed all the proper codecs as listed here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)

---

### Post by ~chinook~ on 2007-05-07
Codecs are all installed I believe.

---

### Post by NeoLithium on 2007-05-07
Well, to make sure, double check with this in a terminal window:
```

sudo aptitude install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll w32codecs

```

As for youtube, make sure you've installed the flash player:
```

sudo aptitude install flashplugin-nonfree

```

---

### Post by tgalati4 on 2007-05-07
What media player are you using?  What version of Ubuntu?  What is your hardware?

It's tough to guess these things.

---

