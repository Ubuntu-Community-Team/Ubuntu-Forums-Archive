---
title: "Installing Wine ?"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by kozak on 2006-01-02
I have tried following the directions on the Wine HQ website.
But, no luck ?

---

### Post by ape on 2006-01-02
Exactly what did you try and what didn't work? I'm using the wine packages from winehq just fine.  No problems.

---

### Post by kozak on 2006-01-02
Well, when I try to install it, I can't find it anywhere. :confused:

---

### Post by ape on 2006-01-02
Make sure that you have the following line in your /etc/apt/sources.list  :

    deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

The run `apt-get update` followed by `apt-get install wine`.  This should install a few packages from the winehq site.

---

