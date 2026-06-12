---
title: "Squeezecenter - will not load from repository for PPC"
date: 2009-09-17
forum: Apple Hardware Users
---

### Post by wadhurstdaisy on 2009-09-17
I'm trying to load Squeezecenter onto an old PPC iBook, not sure whether it is a G3 or G4. The iBook is running 8.04 LTS Hardy Heron.

If I start the Synaptic Package Manager and go into 'settings / repositories' I can add to 'Third Party Software' the entry: -

[CENTER]http//:debian.slimdevices.com stable main[/CENTER]

If I then perform a reload and find Squeezecenter, when I apply the change the following error message appears: -

[CENTER]Failed to fetch [http://debian.slimdevices.com/dists/stable/main/binary-powerpc/Packages.gz](http://debian.slimdevices.com/dists/stable/main/binary-powerpc/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.[/CENTER]

Does anyone know whether: -

1) Squeezecenter will run on my PPC iBook using 8.04?
2) What I need to do to fix this?

Many thanks

Dave.

PS please treat me gently as I'm new to this !

---

### Post by angelus1969 on 2009-09-29
As far as I can see on the website there are only binaries for i386 and x64, sadly no Debian PPC....

---

### Post by wadhurstdaisy on 2009-10-05
Thanks for that, guess I'll have to leave an old 'pc' on all the time just to run my squeezebox :(

---

### Post by jan80 on 2009-10-05
Squeezecenter works fine on PPC platforms, it is all perl scripts (until version 7.3.x). So you can get the source package from their homepage and just install it by yourself. It just might require to build some perl modules...

---

