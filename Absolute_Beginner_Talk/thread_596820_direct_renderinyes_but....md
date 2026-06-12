---
title: "direct renderin:yes but..."
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by soulwind on 2007-10-29
at last I got direct rendering after trying a couple of How-Tos

```
glxinfo | grep direct

```
```
glxinfo | grep direct

```

but I have another problem now. my desktop effects are not working. whn I try to activate desktop effects I get "The composite extension is not available" message.
```
compiz
```
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4152 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 
```

I have tried to install xserver-xgl and I got my desktop effects back....but this time I have lost direct rendering. what should I do?

---

### Post by soulwind on 2007-10-29
Solved :)

---

### Post by lattmau on 2007-11-08
what was your solution?

---

### Post by wlc3069 on 2007-11-08
I have the same problem, what was your solution?

---

