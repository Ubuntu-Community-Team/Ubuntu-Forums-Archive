---
title: "updatemanger won't start."
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by auraithx on 2007-10-18
I tried to update to Fiesty from Edgy last night - I left my comp to download it and when I came back the kernal I was using wouldn't start so I had to use a previous one... now when I try to start update-manager I get this error.

```
glasgowm@glasgowm-desktop:~$ update-manager -d
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 25, in ?
    import pygtk
ImportError: No module named pygtk

```

---

### Post by bonzodog on 2007-10-18
I would actually get Gutsy and go for a clean install now.

Alternatively, you could make sure that python-gtk is installed.

---

### Post by auraithx on 2007-10-18
Would do but I don't have any blank disks...

Is it possible to install to a USB Drive without the need for CDs?

I've had a look on Google but can't see anything that doesn't involve burning to cds first.

---

