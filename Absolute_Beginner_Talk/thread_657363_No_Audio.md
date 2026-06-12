---
title: "No Audio"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by jbmswow on 2008-01-03
For some reason my sound has gone out.  I don't get the boot up sound, the beep for new emails and can't get any music files to play.  I've checked all the settings to make sure nothing got muted, etc.  I'm new to Linux and don't have a clue.  any help would be appreciated.  If I reloaded would that help and would I loose everything or would my files stay intact.
Thanks, 
Jerry

---

### Post by flamelab on 2008-01-03
&#932;ry 

```
alsaconf
```

on terminal , do what it says and then post here again .

---

### Post by jbmswow on 2008-01-03
The response I got was "command not found"

---

### Post by flamelab on 2008-01-03
**Very weird .**

What version of Ubuntu have you installed ?

Have you done this

```
sudo apt-get update

sudo apt-get upgrade 

```
 ???

Go to Synaptic and please tell me if there is "alsa" installed .

---

### Post by jbmswow on 2008-01-03
I have 7.10 with all updates.

---

### Post by metalpancake on 2008-01-03
you can try 'alsamixer' in the terminal.

---

