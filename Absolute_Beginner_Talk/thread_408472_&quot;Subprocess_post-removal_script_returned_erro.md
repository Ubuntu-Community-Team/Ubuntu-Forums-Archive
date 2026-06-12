---
title: "&quot;Subprocess post-removal script returned error exit status 1&quot;"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-04-13
In Synaptic, I have a couple of programs that show in Not Installed (Residual Config).

When I try and remove them, I get the error message above.

Doing apt-get remove tells me the progs are no longer there, so how do I remove them (if I can!) from the list in Synaptic?

---

### Post by Seisen on 2007-04-13
Try using these and see if it removes them.

```
sudo apt-get autoclean 
```
```
sudo deborphan | xargs sudo apt-get -y remove --purge 
```

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html")

---

### Post by qprfact on 2007-04-13
Sadly, no, they didn't!

---

