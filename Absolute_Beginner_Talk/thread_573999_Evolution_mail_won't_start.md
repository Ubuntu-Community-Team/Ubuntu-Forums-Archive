---
title: "Evolution mail won't start"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by orduek on 2007-10-12
Hi,
I installed Ubuntu a week ago and since then I'm unable to start Evolution mail.
When trying to start it from terminal i get the following message:
CalDAV Eplugin starting up ...
Segmentation fault (core dumped)

Can anyone help me please?

---

### Post by aspen_dv on 2007-10-12
Try to remove Evolution and reinstall it.

---

### Post by orduek on 2007-10-12
Tried it.
didn't work.

---

### Post by orduek on 2007-10-14
does anyone has the answer?

---

### Post by Austin_KW on 2007-10-14
try killing any running evolution processes
```
sudo killall -r evolution*

```
Then try restarting evolution

---

### Post by orduek on 2007-10-18
didn't work either.

---

### Post by Austin_KW on 2007-10-18
Yes, just after my reply it happened to me. 
The killall did not work. 
I could not find any open files or locks. After looking at it for 10 mins I could not find what resource it was blocking on. I got lazy, and just rebooted to fix it.

---

### Post by gmccague on 2008-01-29
> **Austin_KW said:**
> try killing any running evolution processes
```
sudo killall -r evolution*

```
Then try restarting evolution

also do

```
sudo killall -r gnome-keyring*
```

This worked for me. The problem seems to be with the gnome-keyring integration with Evolution. Hopefully someone will fix it soon.

---

