---
title: "[SOLVED] No win32codecs in repos?"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by MangasColoradas on 2007-12-16
How can I get them please?

,

---

### Post by wormser on 2007-12-16
This [blog]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html") has a tutorial.  You can skip the mplayer part if you want.

---

### Post by gupta_sumesh63 on 2007-12-16
Look for w32codecs and not win32codecs.
add mediubuntu reository to your sources.lst
then run the following codes:(one after the other)

> sudo apt-get update

> sudo apt-get upgrade

> sudo apt-get install w32codecs

enjoy!!!

---

### Post by Kingsley on 2007-12-16
ubuntu-restricted-extras may be what you're looking for.

---

### Post by Sef on 2007-12-16
> sudo apt-get install w32codecs

> ubuntu-restricted-extras may be what you're looking for.

The win32codecs are not in the repositories.

---

### Post by MangasColoradas on 2007-12-16
I have restricted extras. :)

I followed the blog as it mentioned what I assume were DVD codecs as well.

Anyway, it worked. I now have sound on .wmv files.

Thanks guys.
:KS

---

### Post by MangasColoradas on 2007-12-16
I now seem to be having trouble with mplayer plugin in firefox, could it be a conflict with gstreamer and the w32 codecs?

It crashed when I tried to stream BBC radio, but it hasnt done it again.

Maybe its OK now....

---

### Post by wormser on 2007-12-16
Just in case the problem arises again.  When I installed mplayer I had to uninstall the totem firefox plugin to get it working right.  I believe that package is called totem-mozilla.

---

### Post by Sef on 2007-12-16
BBC has been working off and on for me.  Perhaps as more video is converted to flash, this problem will disappear.

---

### Post by MangasColoradas on 2007-12-16
I already removed totem firefox plugin wormser.

Thanks sef, it seems to be working now, anyway.

I had read somewhere about gstreamer and w32codecs causing problems with both installed (cant remember what problems), so thats why I was concerned.
:)

---

### Post by Sef on 2007-12-16
You're welcome.  I'm glad all is working fine for you.

---

