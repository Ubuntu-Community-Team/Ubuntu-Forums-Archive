---
title: "How can I maximize space on 4GB?"
date: 2004-12-31
forum: Apple PPC Users
---

### Post by phatbob on 2004-12-31
I have Ubuntu loaded on my iMac G3 233MHz (rev A), and I am very pleasantly surprised at the performance. It actually runs quite acceptably!

But I'd like to maximize performance and save some disk space as well-- I have only the original 4GB hd on this thing installed.

Any suggestions?

Also, is it "safe" to delete the .deb files in /var/cache/apt/archives?

Thanks...

---

### Post by az on 2004-12-31
Yes, delete the .deb files.  You still have them on the cd.  You can also remove openoffice and install abiword in its place.

You will save disk space and have a top-notch word processor that does not suck up all your free memory.

---

### Post by Laf on 2004-12-31
Do not touch apt-get files as you want.

Do : sudo apt-get clean

And apt-get will clean this directory.

Then, as said upper, you can replace OpenOffice by Abiword, also try Gnumeric. Something also interesting, delete Firefox and install "epiphany-browser" which is lighter.

After all of this you'll have to look at all programs installed, for example in /etc/init.d all this programs runs at startup, you can clean all of this (as before, never delete files, use programs to do this).

I can't tell you now what to delete, i'm a "one week Ubuntu user" but i plan to clean all of this (useless support for RAID, NTP etc.). I'll maybe post a topic about it.

---

### Post by phatbob on 2005-01-01
[QUOTE=Laf]I can't tell you now what to delete, i'm a "one week Ubuntu user" but i plan to clean all of this (useless support for RAID, NTP etc.). I'll maybe post a topic about it.[/QUOTE]

Great! If you do post a topic, will you please also let us know with a short post in this thread telling us the subject line of the new one? Thanks.

---

