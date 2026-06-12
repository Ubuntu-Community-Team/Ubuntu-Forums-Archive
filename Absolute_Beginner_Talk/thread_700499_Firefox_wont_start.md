---
title: "Firefox wont start"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by nemodot on 2008-02-18
Hi, i recently installed Kubuntu because i didnt had the ubuntu cd. Then i installed Ubuntu-desktop and i am now in ubuntu.

The problem is that when i click on the Firefox icon, the program wont start. It says "Starting Web Browser Firefox" but it closes...

Firefox doesnt appear on the process list after that.

I tried reinstalling it, but the problem persist.

That's all.
Sorry about my limited english.

---

### Post by smartboyathome on 2008-02-18
Try running firefox in a terminal and see if there are any errors.

---

### Post by FuturePilot on 2008-02-18
See if creating a new profile will work
```
mv ~/.mozilla ~/.mozilla_old
```
Try starting Firefox then.

---

### Post by nemodot on 2008-02-18
> **FuturePilot said:**
> See if creating a new profile will work
```
mv ~/.mozilla ~/.mozilla_old
```
Try starting Firefox then.

Thank you!
It Worked.

Why this happened? I want to know what was the error and why it ocurred.

---

### Post by smartboyathome on 2008-02-18
> **nemodot said:**
> Thank you!
It Worked.

Why this happened? I want to know what was the error and why it ocurred.

It is probably configured for Kubuntu, and the configuration is incompatible with (GNOME) Ubuntu.

---

