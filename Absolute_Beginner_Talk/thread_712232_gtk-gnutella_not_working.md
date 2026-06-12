---
title: "gtk-gnutella not working ????"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by broekskw on 2008-03-01
ok this is funny, this program has been working for me for months but all of a sudden it's not, did nothing to change things, just updated threw update manager everything there was an update,
open this in a terminal,can anyone read my screen shot and explain to me what is not happening:guitar:

---

### Post by lloyd_b on 2008-03-01
There's nothing on the screenshot that indicates a critical failure.  In short, I don't see a reason for GtkG to not start.

Question:  How long did you let it go before giving up?  Some versions of GtkG took a while to initialize.

One thing that's a little odd - it didn't find "sha1_cache", which would be a bit odd if you've used GtkG before (unless you aren't sharing any files).

One suggestion - In a terminal window:
```
cd
mv .gtk-gnutella .gtk-gnutella.old
```

This will move the settings directory to a new name, and make it a "clean start".  If there's something weird in the configuration, this will clear it.

Lloyd B.

---

### Post by broekskw on 2008-03-01
lloyd_b thanks for your reply, so after about 25 minuets left  the program started to down load and works just fine, never took that long before, will try your command in terminal

again thanks
:guitar:

---

### Post by cbiere on 2008-03-01
If it is working now, you should definitely not scrap your configuration as suggested by lloyd_b because it will cause more problems than it solves. gtk-gnutella will not know a single peer anymore and may fail to bootstrap. None of your files are shared anymore, all your download sources are lost and once you share files again, all of them have to be indexed again which can easily take hours. Scrapping your configuration is the last resort. It likely never helped anyone, if it seemed have helped, it was most-likely just a coincident and simply restarting it would have had the same effect.

Anyway, you did not actually explain what was not working. Was the application window not appearing? Was it just not connected to any peers? Was it trying to connect to any? Or where you just not getting any search results? Or just not downloading? It is not clear, what you mean with "not working".

---

### Post by broekskw on 2008-03-01
hi cbiere, the program would not do anything, download that is,most of the time after running this program could download in as little as two minutes, just know it take at least 25 minutes to start working, 

:guitar:

---

### Post by lloyd_b on 2008-03-02
> **cbiere said:**
> If it is working now, you should definitely not scrap your configuration as suggested by lloyd_b because it will cause more problems than it solves. gtk-gnutella will not know a single peer anymore and may fail to bootstrap. None of your files are shared anymore, all your download sources are lost and once you share files again, all of them have to be indexed again which can easily take hours. Scrapping your configuration is the last resort. It likely never helped anyone, if it seemed have helped, it was most-likely just a coincident and simply restarting it would have had the same effect.
.
 
The suggestion was to "move" the config files, not scrap them.  I wasn't explicit, but my intention was, if this cleared the issue, to have him move them back selectively, and see when/if the problem recurs.

And there *were* cases (in SVN) where this would make a difference.  For instance, that bug that resulted in GtkG crashing if there was a partially-completed download of a large file...

Lloyd B.

---

### Post by cbiere on 2008-03-02
I didn't mean to imply that your suggestion was terrible but it should be the "last resort". It's just that I've read this suggestion so often elsewhere that you could think it's the magic solution for everything like rebooting solves everything under Windows.

Every rule has its exception. Scrapping the complete directory was overkill in that case as well though. Also it wouldn't solve the issue, it would just make it go away for the moment. What's important though is that if someone hadn't submitted a detailed bug report, it might have never been fixed. Users reporting problems are a precious resource, most of them wouldn't bother and just switch to something else. Therefore it's important that one tries to analyze a problem before suggesting workarounds.

There's a clever quote, you can see regularly in someone's quit message at gtk-gnutella's IRC channel:
"You can't fix a problem you don't understand, you can only make it stop happening."

---

