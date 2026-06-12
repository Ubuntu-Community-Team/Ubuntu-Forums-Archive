---
title: "[SOLVED] gtk-gnutella serious problem"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-07-26
I installed GTK-Gnutella, it works and all - I get search results and downloads happen at a decent speed. I want to try it out for at least a while despite is complex interface, but I can't figure out how to filter search results.
Whenever I search for something, I get relevant results but also a whole lot of other rubbish - such as "find free mp3 cds", "get IE features" and pornographic material which I absolutely do NOT want in my search results.
What do I do??
Please help, thanks.

---

### Post by pyros on 2007-07-26
It is possible that is is not currently capable of that. Have you tried asking on the gtk-gnutella mailing lists?

---

### Post by deadgobby on 2007-07-26
Ya GTK does pick up every thing under the sun. Who would of thought if you type in Surf City you get porn. Any ways this link may help
[http://www.gnutellaforums.com/gtk-gnutella-linux-unix/48766-help-filters.html](http://www.gnutellaforums.com/gtk-gnutella-linux-unix/48766-help-filters.html)

Gobby

---

### Post by deadgobby on 2007-07-26
Oh be careful of mpegs files. It may say one thing and you open it up and it is porn. You may do better if you a bit torrent like [http://thepiratebay.org/](http://thepiratebay.org/)

---

### Post by cbiere on 2007-07-26
Are you using the latest version of gtk-gnutella that is 0.96.4? That one should filter out most spam by default. You can also fetch the newest host blacklist from here:

[https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/extra_files/hostiles.txt](https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/extra_files/hostiles.txt)

Put this file into ~/.gtk-gnutella/. You'll have to restart gtk-gnutella the first time you create this file. Otherwise, it's reloaded on the fly. This will at least get you rid of the kind of spam you mentioned.

---

### Post by kleo skywalker on 2007-07-26
> **cbiere said:**
> Are you using the latest version of gtk-gnutella that is 0.96.4? That one should filter out most spam by default. You can also fetch the newest host blacklist from here:

[https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/extra_files/hostiles.txt](https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/extra_files/hostiles.txt)

Put this file into ~/.gtk-gnutella/. You'll have to restart gtk-gnutella the first time you create this file. Otherwise, it's reloaded on the fly. This will at least get you rid of the kind of spam you mentioned.

Thanks very much. I did this, and ran a couple of searches to check - no more rubbish.

---

