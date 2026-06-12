---
title: "Annoying sound on start"
date: 2011-04-06
forum: Apple Hardware Users
---

### Post by Sasha55 on 2011-04-06
If you don’t like the sound on very beginning when your Mac start (on Intel based Macs) just do:
nvram SystemAudioVolume=%00

is there some possibility to integrate nvram update in rEFIt on startup ?

---

### Post by FoxEWolf on 2011-04-06
> **Sasha55 said:**
> If you don&#8217;t like the sound on very beginning when your Mac start (on Intel based Macs) just do:
nvram SystemAudioVolume=%00

is there some possibility to integrate nvram update in rEFIt on startup ?

I am unsure but if all else fails, you can try to just mute the computer before shutting down. That should save it to 0% I am not concerned with the issue and never bothered with the boot chime before.

---

### Post by sauferkel on 2011-04-07
i guess you still also have osx installed, so maybe this fix here helps you ;)

[http://www5e.biglobe.ne.jp/~arcana/StartupSound/index.en.html]("http://www5e.biglobe.ne.jp/~arcana/StartupSound/index.en.html")

---

### Post by FilliPs on 2011-04-10
I think you can find here some useful information [http://refit.sourceforge.net](http://refit.sourceforge.net)

---

### Post by Sasha55 on 2011-04-13
@sauferkel
it's not working on intel,

---

