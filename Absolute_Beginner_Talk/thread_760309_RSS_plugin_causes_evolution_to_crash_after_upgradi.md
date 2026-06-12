---
title: "RSS plugin causes evolution to crash after upgrading to 8.04 rc"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by lucasl on 2008-04-20
Hi,
I just upgraded to hardy heron's release candidate, and now evolution won't start due to the rss plugin.
Here is what happens. When I run evolution, all my feeds start downloading and all the ones from digg start tripling and quadrupling with duplicates (see attachment). Here is the terminal output
```
computer:~$ evolution
RSS Plugin enabled
RSS Plugin enabled
Reading RSS articles...
feed PAL Gaming Network
feed Dilbert
feed Explosm.net
feed Digg / Technology
feed Digg / Gaming
Segmentation fault

```
If I run  evolution --disable-eplugin, everything works fine, and I can see all the duplicates.
Try getting evolution 2.22.1 and evolution-rss 0.0.8 from the hardy repos to reproduce.

Thanks,
Lucas

---

### Post by lucasl on 2008-04-20
Update:
I disabled all the feeds, and it didn't crash, so the problem occurs when fetching. I tried enabling the feeds one by one, and it was working (although it said cancelled in the fetching rss bit, but I still got the articles) until I enabled Digg / Gaming.

Some more confusing console output: 
```
feed xkcd.com
BBDB spinning up...
component_id:OAFIID:GNOME_Evolution_RSS:2.22
rf->0x81112d8

(evolution:16195): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.3/gobject/gsignal.c:1669: signal `value-changed' is invalid for instance `0x87a9398'
feed PAL Gaming Network
component_id:OAFIID:GNOME_Evolution_RSS:2.22
rf->0x81112d8

(evolution:16195): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.3/gobject/gsignal.c:1669: signal `value-changed' is invalid for instance `0x89875e8'
component_id:OAFIID:GNOME_Evolution_RSS:2.22
rf->0x81112d8

(evolution:16195): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.3/gobject/gsignal.c:1669: signal `value-changed' is invalid for instance `0x8daa140'

component_id:OAFIID:GNOME_Evolution_RSS:2.22
rf->0x81112d8

(evolution:16195): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.3/gobject/gsignal.c:1669: signal `value-changed' is invalid for instance `0x8eb4bb0'

```

Thanks

---

### Post by KenDiPietro on 2008-04-25
> **lucasl said:**
> Hi,
I just upgraded to hardy heron's release candidate, and now evolution won't start due to the rss plugin.
Here is what happens. When I run evolution, all my feeds start downloading and all the ones from digg start tripling and quadrupling with duplicates (see attachment)...

In my case, if I hit the Send/Receive button Evolution crashes. However, if I uncheck the Evolution-RSS plugin from my Plugin box all appears to be well. I decided to post this here as independent confirmation of the problem.

---

### Post by lucasl on 2008-04-26
I'm bumping this, as a third person now has this problem as well: [http://ubuntuforums.org/showthread.php?p=4797810](http://ubuntuforums.org/showthread.php?p=4797810)

---

### Post by jimfarr on 2008-04-26
Same problem here;
Linux 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
Evolution 2.22.1

Enable RSS plug-in and Evolution crashes, disable it and all is well.

jimf

---

### Post by lucasl on 2008-05-01
Bump again. Is there no solution to this?
It seems like a massive bug to get past rc.

---

### Post by TitanKing on 2008-05-05
Oops same problem here, Digg also makes mine crash (Top Stories). The only work-around is to disable Digg. But it is cool for now as all top stories are;

Obama, Hillary, Hillary, Obama, Obama, Obama, Hillary, Obama, etc... etc... etc...

---

### Post by TitanKing on 2008-06-20
This problem still persists in Stable Hardy, use this to fix problem:

[http://ubuntuforums.org/showthread.php?p=5223926#post5223926](http://ubuntuforums.org/showthread.php?p=5223926#post5223926)

---

