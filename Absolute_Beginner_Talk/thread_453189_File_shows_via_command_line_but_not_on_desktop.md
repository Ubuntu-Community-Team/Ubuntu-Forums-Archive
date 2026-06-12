---
title: "File shows via command line but not on desktop"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by xyz on 2007-05-24
Hi all,

I wonder if any of you would have an explanation for this:
In a terminal, I run:
```
cd Desktop
```
and then:
```
ls
```
to list what's on my desktop.
The output is:
> Unsaved Document 1~

but this "Unsaved Document 1~" file does not show on my desktop??

---

### Post by stefaan.dutry on 2007-05-24
It seems to be a temporary recovery file of a new document that hasn't been saved yet.

But then again i'm not sure.

---

### Post by xyz on 2007-05-24
Thanks for the reply.

OK I tried this. I open nautilus (Alt + F2), ran *gksudo nautilus* and went to /home/user/Desktop and, indeed, the file was there.

I deleted and it is now completely gone. Still it doesn't explain much!

---

### Post by mattmole on 2007-05-24
Files ending in ~ are indeed recovery files. There is little point showing them in nautilus as they are for safety purposes - not everyday use.

---

### Post by xyz on 2007-05-24
Thanks for your time, guys!

---

