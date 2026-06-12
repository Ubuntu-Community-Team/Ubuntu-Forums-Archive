---
title: "Problems with sound juicer..."
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Roen hayden on 2007-06-25
Ok i have the mp3 codecs installed and i know how to add MP3  support to sound juicer but when i add MP3 it will not let me edit it it brings it the window to edit and it freezes it any ideas?

---

### Post by odiseo77 on 2007-06-25
Hi, if you're on Feisty and want to add capability to encode cd's to mp3's (this is what you want, if I don't understood you bad, right?), simply install ***gstreamer0.10-plugins-ugly*** and ***gstreamer0.10-plugins-ugly-multiverse*** packages, restart sound juicer, and automagically you'll find mp3 support in the preferences.

Regards.

---

### Post by mitch.c on 2007-06-25
You don't mention the distribution/release (dapper, edgy, feisty, etc) you are using, or if you are able to rip CD's, but I had a similar problem on edgy... I could not rip a CD, nor could I edit the gnome-sound-properties without locking up not only the app, but my PC. This was caused by a problem with libcdparanoia1 and cdparanoia. I had to downgrade these two packages to resolve.

The package version in question were: 3.10+debian~pre0-4build1~edgy1

If this sounds like it may be the cause of your issue, downgrade to: 3a9.8-13

Again, I am running Edgy.

---

### Post by Roen hayden on 2007-06-25
i'm using feisty...

---

### Post by odiseo77 on 2007-06-25
> **Roen hayden said:**
> i'm using feisty...

So, did you try what I suggested above??

---

### Post by Roen hayden on 2007-06-25
> **odiseo77 said:**
> Hi, if you're on Feisty and want to add capability to encode cd's to mp3's (this is what you want, if I don't understood you bad, right?), simply install ***gstreamer0.10-plugins-ugly*** and ***gstreamer0.10-plugins-ugly-multiverse*** packages, restart sound juicer, and automagically you'll find mp3 support in the preferences.

Regards.

i cant find those in Add/remove applications...

---

### Post by Roen hayden on 2007-06-25
Never mind i got it to work thanks!!!!

---

### Post by mitch.c on 2007-06-26
How about sharing the fix? :p

---

