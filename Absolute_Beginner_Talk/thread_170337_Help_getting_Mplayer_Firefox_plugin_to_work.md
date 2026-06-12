---
title: "Help getting Mplayer Firefox plugin to work"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by Dusk2k2 on 2006-05-04
Okay, I've installed the mplayer firefox plugin from the repository, but when I go to visit websites, such as Apples movie trailers, the screen just says "no picture" where a streaming video should be playing.  How can I get mplayer plugin working so that I can view streaming trailers on the apple website?

I'm running the Ubuntu Dapper Drake Beta

---

### Post by tonyr on 2006-05-04
You probably need the non-free codecs.  Add

```

## Specifically for w32codecs
## Penguin Liberation Front
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

```
to **/etc/apt/sources.list**, then

```

sudo apt-get update
sudo apt-get install w32codecs

```

EDIT: I know it says **breezy**, but it works anyway.

---

