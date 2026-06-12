---
title: "Restarting"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2006-04-19
Could someone explain to me in idiot terms why Ubuntu never needs to restart after updates and software installs and Windows does?

---

### Post by Stewart on 2006-04-19
Linux good.

Windows bad. :twisted: 

I hope this helps.

Stewart

---

### Post by fng on 2006-04-19
Linux only needs a restart after a new kernel is installed.

Why windows needs a reboot after each update? You'll get the answer from microsoft's website :)
[http://support.microsoft.com/kb/887012](http://support.microsoft.com/kb/887012)

---

### Post by wylfing on 2006-04-19
The linked KB article might be polishing the turd. I don't really know -- I am not that up on Windows internals -- but it's possible that there's no way to know what kind of tangled web of process dependencies exist while Windows is up and running, and so the easiest way to restart the necessary processes is just to restart the entire OS.

In Linux, most processes tend to be pretty self-contained. You can safely restart "core" things like printing or networking, because the functionality is atomic. But even in Linux there are times when tracking down all the necessary services is just too much of a pain, and you go ahead and reboot the box to save time.

---

