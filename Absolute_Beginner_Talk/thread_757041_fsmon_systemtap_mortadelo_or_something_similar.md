---
title: "fsmon systemtap mortadelo or something similar"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by komputes on 2008-04-16
I'm looking for an application that can keep tabs on the filesystem and notify (print a line) every time a file is modified, added or removed. I remember using something lise this, I think it was called fsmon. Does anyone have instruction to install/use one of the following or something similar on Ubuntu?

fsmon
systemtap
mortadelo

---

### Post by terrukallan on 2008-04-16
I have not used any of these myself, but you might want to take a look at:
systraq
iwatch
fileschanged

---

### Post by komputes on 2008-04-17
fileschanged looks interesting but I can't get it to work correctly:

I have a file with a list of files (one per line) and I want all of them to be monitored while I run a process, so I have tried using:

```
sudo fileschanged -pa --timeout=999 --filelist=FILE
```

The issue is that I get the error:

```
Segmentation fault (core dumped)
```

---

