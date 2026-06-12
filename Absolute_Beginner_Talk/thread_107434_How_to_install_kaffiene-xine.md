---
title: "How to install kaffiene-xine?"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by derekho55 on 2005-12-23
Hi..
I have a Kubuntu 5.10.

I tried to do :
sudo apt-get install kaffeine-xine

after I uninstalled kaffeine-gstreamer. But somehow I get this message: 
"Package kaffeine-xine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kaffeine-xine has no installation candidate"

What does this mean?
Is this method correct?

Thanks.

---

### Post by MartinG on 2005-12-23
When you uninstalled kaffeine-gstreamer, did kaffeine get removed as well (which would explain it)?  It's sometimes easier to sort this out with Synaptic -- search for kaffeine and see what's installed and what isn't.

---

### Post by derekho55 on 2005-12-23
Hi, thanks for replying.

I reinstalled Kaffiene .. (and it automatically reinstalled gstreamer as well) and with this, I tried to install kaffine-xine, and it still produced the same result.

Any further Ideas?

---

### Post by Estariel on 2005-12-23
Hi!
I think you need not uninstall the gstreamer kaffeine.

Just click "Settings" -> Player Engine and select xine. (When you have xine installed this should become available)

I'm not sure if this works on Ubuntu, it works on my Gentoo box though...

---

### Post by MartinG on 2005-12-23
[QUOTE=derekho55]Hi, thanks for replying.

I reinstalled Kaffiene .. (and it automatically reinstalled gstreamer as well) and with this, I tried to install kaffine-xine, and it still produced the same result.

Any further Ideas?[/QUOTE]My next thought is -- have you got the necessary repositories in your sources.list? AFAIK kaffeine-xine is in the universe repository, which is not enabled by default.  If you're not sure what you're doing here, the unofficial Ubuntu Guide has instructions:

[http://makuchaku.info/amnesty/#extrarepositories](http://makuchaku.info/amnesty/#extrarepositories)

---

### Post by derekho55 on 2005-12-23
Thank you.

Now I can play AVI files~

I just need to solve my sound problems ahaha. I don't seem to have any sound output from any program. Oh well, I probably need to configure some sound settings, and install some files.

Thank you again.

---

