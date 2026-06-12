---
title: "Folder not showing contained files"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Vekin on 2007-05-03
I extracted a video into my video folder, went to that folder, and there's nothing in it.  I extracted it to my desktop, and tried to move it into my video folder, and it said that I would have to replace that same video that was already there.  How do I fix this?

---

### Post by nanotube on 2007-05-03
> **Vekin said:**
> I extracted a video into my video folder, went to that folder, and there's nothing in it.  I extracted it to my desktop, and tried to move it into my video folder, and it said that I would have to replace that same video that was already there.  How do I fix this?

what does it say from the commandline?
try
```
ls -al /path/to/your/folder
```

---

### Post by coolcalt on 2007-05-03
> **Vekin said:**
> I extracted a video into my video folder, went to that folder, and there's nothing in it.  I extracted it to my desktop, and tried to move it into my video folder, and it said that I would have to replace that same video that was already there.  How do I fix this?

is it on your desktop?

if in firefox check Edit - Prefs - Main - Downloads

I had the same problem, but I was confused by the new way the filesystem works to windows.

---

### Post by Vekin on 2007-05-03
Hm, I tried as you suggested, and it lists the files as being in there.  It's just not showing them when I open them in Nautilus...

Any ideas?

It might be good to note that I'm downloading something to that folder via Ktorrent.

---

### Post by nanotube on 2007-05-03
under nautilus, did you make sure to do view>show hidden files ?
also for good measure, do view>view as list

---

