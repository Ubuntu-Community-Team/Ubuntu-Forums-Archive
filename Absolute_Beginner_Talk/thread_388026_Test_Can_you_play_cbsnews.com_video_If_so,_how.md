---
title: "Test: Can you play cbsnews.com video? If so, how?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by pdxuser on 2007-03-19
I'm trying to play video from CBSNews.com.  I have mplayer, which plays the audio but not the video.  I'm wondering if anyone has a setup that works, and if so, what it is so the rest of us can copy it?

[[Test your system!]("http://www.cbsnews.com/sections/i_video/main500251.shtml?channel=eveningnews")]

---

### Post by k1001001 on 2007-03-19
There's a Linux version of RealPlayer that should make this video work when installed. You can download it from the RealPlayer website.

---

### Post by jordanmthomas on 2007-03-19
I can play it using mplayer-plugin.
I'm also using Arch Linux if that matters.

---

### Post by pdxuser on 2007-03-19
Hm, I'd rather not change distros just for RealMedia.  I wonder why RealPlayer isn't listed in Add/Rm Apps or Synaptic?  (Same question for [Pixel]("http://www.kanzelsberger.com/pixel/?page_id=5"), which looks like a dramatic improvement over GIMP.)  I have Uni-/Multiverse OK'd...?

---

### Post by jordanmthomas on 2007-03-19
If you have all the repositories, try installing mplayer-plugin (or something similarly named)

Pixel is not free (beer or freedom) and only offers a trial version, so that's probably why it's not included.

---

### Post by riven0 on 2007-03-19
You can also try the helix-player, which is able to play RAM files. Look for *helix-player* and *mozilla-helix-player*.

---

### Post by DarkN00b on 2007-03-19
Codecs via Automatix + mplayer plugin for FF = (the video played just fine)

---

### Post by r4ik on 2007-03-19
Mplayer Icewaesel Debian.
Works just fine.

---

### Post by pdxuser on 2007-03-19
Ugh.  I went to download Automatix, which wan't in Add/Rm Apps, and was told to follow a [six-step process]("http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29") in Terminal.  After getting to the sixth step, I see:

> The following NEW packages will be installed:
  automatix2 gnome-media-common libgda2-3 libgda2-common libgdl-1-0
  libgdl-1-common libgksu1.2-1 libgksuui1.0-1 libgnome-media0
  libgtksourceview-common libgtksourceview1.0-0 libmetacity0 libnautilus-burn4
  libpanel-applet2-0 libwnck-common libwnck18 libxres1 metacity-common
  python-gnome2-desktop python-gnome2-extras

Obviously, if I wanted the GNOME Desktop I wouldn't be using Xubuntu.  Now I don't even know how to undo whatever I did in steps 1 through 5.

---

