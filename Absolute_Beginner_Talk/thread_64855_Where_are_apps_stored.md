---
title: "Where are apps stored?"
date: 2005-09-12
forum: Absolute Beginner Talk
---

### Post by open-flanker on 2005-09-12
How does Ubuntu store apps on the disk? For example, programs in Win are stored (unless you change the default option) to Program Files. The problem is, for me noob dumb ass, that the program names are meaningless. If I want to run a program from the CLI the hardest thing is finding it. I guess it is down to using GUI's all these years and being able to do it half asleep.

I seem to think (rightly or wrongly) that they are in etc/bin or something like that. Is this right?

---

### Post by KingBahamut on 2005-09-12
exectuables are stored in 

/usr/bin
/usr/sbin
/sbin 

but everything in /usr/bin is symlinked, so whatever you type in whatever Command line will run as though you were in that directory.

---

### Post by lao_V on 2005-09-12
You can check out one of the many filesystem guides on the net [here]("http://www.micronux.com/catalog/article_info.php?articles_id=6")

---

### Post by numberexhaust on 2005-09-12
if you're looking to run programs, just use the command line.  if you're looking to install and uninstall, the best way to do it is using synaptic package manager.

---

### Post by aysiu on 2005-09-12
You don't need to use the CLI to launch apps.
That said, most apps live in either /bin or /usr/bin.
But you don't need to know where the app lives in order to run it. Whatever it's "called" in Synaptic is usually the name by which you can launch it. Just "run program" and type in the name of the program--you don't need the location.

---

