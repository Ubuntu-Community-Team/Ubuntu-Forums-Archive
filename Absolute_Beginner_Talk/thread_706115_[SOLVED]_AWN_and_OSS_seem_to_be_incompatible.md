---
title: "[SOLVED] AWN and OSS seem to be incompatible"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by jonnywombat on 2008-02-24
I have an issue when trying to run AWN and OSS together..

Awn has become an essential part of my install and a must have. I also have issues with alsa and my sound card (nvidia hda) around jack sensing. Having tried every single option I can find here the only cure that works for me is using OSS instead.

However when I install OSS it breaks AWN, some applets fail and I cannot access the AWN manager at all. 

If I do a clean install of AWN on a machine with OSS then AWN works ok, but OSS fails, I have no sound and when trying to play mp3's I get a "null" error...

I would love to get both co existing...

Jonny

---

### Post by jonnywombat on 2008-02-24
I have managed to find a work around to get AWN and OSS working together, with the help of **cesium at the OSS forums** and [B]moonbeam at the AWN forum
[/B]
Basically, it appears AWN has alsa dependacies which get changed when you install OSS via the deb file..

However this can be overcome

First visit this guide and install AWN as per the instructions...

[http://ubuntuforums.org/showthread.php?t=385981&highlight=install+awn](http://ubuntuforums.org/showthread.php?t=385981&highlight=install+awn)

Once completed I would edit your sources.list and hash out the AWN repos as I *guess *AWN updates may break OSS

To install OSS **DO NOT USE THE .DEB FILE**
Instead visit here and run the script

[http://paste.ubuntu-nl.org/56973/](http://paste.ubuntu-nl.org/56973/)

This seems to work for me, but I guess your mileage might vary.

[B]DO NOT INSTALL  AWN after OSS as this will break OSS!!!
[/B]
[SIZE="1"]for more information visit

[http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=1623&page=1&isLive=true](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=1623&page=1&isLive=true)
[http://4front-tech.com/forum/viewtopic.php?t=2496&sid=299ede91db72b1fc48ef9d6c91719893](http://4front-tech.com/forum/viewtopic.php?t=2496&sid=299ede91db72b1fc48ef9d6c91719893)[/SIZE]

---

### Post by Bogus83 on 2008-04-09
Let's just say, hypothetically speaking of course, someone hadn't read this guide, and installed OSS, followed by AWN, only to find that OSS stopped working.  What would be the best remedy?  Complete removal and reinstallation of OSS?

---

### Post by SoulSmasher on 2008-04-10
is this solution is also acceptable for awn-curves ?

---

