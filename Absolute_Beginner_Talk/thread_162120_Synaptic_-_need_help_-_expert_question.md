---
title: "Synaptic - need help - expert question?"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2006-04-18
Back again with the same problem.
Installation of 'avidemux' went awry
Synaptic will not load and  shows this:
[COLOR="Blue"]E: The package avidemux needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.[/COLOR]
Have tried to uninstall/reinstall and manually remove all avidemux files to no avail.
(using automatix/dpkg/apt-get etc)

**Question: Can I edit some file that Synaptic uses so it ignores this botched install and loads the cache etc ?**
I did try (from the Synatic help page)  [COLOR="Blue"]apt-get install -f[/COLOR] to no avail.
I searched for files containing the word 'avidemux' and found these and my question is can I just edit out the avidemux reference in one or more to get back my Synaptic ?

var/lib/dpkg/info/automatix.list
/var/lib/dpkg/status
/var/lib/dpkg/available
/var/lib/dpkg/available-old
/var/lib/gstreamer/0.8
/var/cache/apt/pkgcache.bin
/usr/lib/gstreamer0.8/libgstavi.so
/usr/loca/automatix/autoscript

signed "getting frustrated" ](*,)

---

