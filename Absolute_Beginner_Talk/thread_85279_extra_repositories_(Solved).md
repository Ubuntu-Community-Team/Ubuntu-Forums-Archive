---
title: "extra repositories? (Solved)"
date: 2005-11-02
forum: Absolute Beginner Talk
---

### Post by akurashy on 2005-11-02
i'm kinda annoyed, because when im checking ubuntuguide it says sudo "this" well i do so, when it try to get the package it doesn't find it. is there a way where i can get latest apps. like xchat 2.4.5 etc etc :(. and other things :(

---

### Post by teaker1s on 2005-11-02
could always download and either compile or run the binary from the software website if it's not in repositories

---

### Post by emperor on 2005-11-02
[quote=akurashy]i'm kinda annoyed, because when im checking ubuntuguide it says sudo "this" well i do so, when it try to get the package it doesn't find it. is there a way where i can get latest apps. like xchat 2.4.5 etc etc :(. and other things :([/quote]

xchat is in the universe repo.
You will need to add "universe" to /etc/apt/sources.list
There are comments in the "sources.list" file concerning how to do this.

To get access to all available packages, add "multiverse" repo too. Just add the keyword "multiverse" at the end of the line with "universe".

After saving your edits, start Synaptic and do a "Reload", then search for "xchat".

#sources.lst: example adds!
================
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by akurashy on 2005-11-02
Thanks!

---

