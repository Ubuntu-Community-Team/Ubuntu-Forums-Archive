---
title: "how to fetch cover from rythmbox to amarok"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2008-01-09
since the amarok cover manager isn't doing a lot of things,i thought it would be good idea to ...import them
any ideas how to do it?

---

### Post by lian1238 on 2008-01-09
I'm not so sure that Rhythmbox finds covers better than Amarok, since Amarok even has a cover manager.

Anyway, here's how to do it:
Play a song from the album in Amarok.
Make sure you can access the Context tab on the left.
Go to Context and right click on the missing cover, then set custom cover.
(in the rare case that the song does not have an album name, this button is unavailable)
The Rhythmbox covers can be found at
```
~/.gnome2/rhythmbox/covers
```
If, for some reason it's not there, run this:
```
locate /rhythmbox/covers
``` and you'll see the correct directory.

---

