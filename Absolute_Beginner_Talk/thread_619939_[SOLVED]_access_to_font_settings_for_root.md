---
title: "[SOLVED] access to font settings for root"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by shuttleworthwannabe on 2007-11-22
Sorry to bother again,

I wish to set fonts for root functions (terminal, synaptic, update manager, etc.). I have custom fonts for user, and wish to set the same for root (reason: root has monospace and sans as default, I (user) have Tahoma as default, I want them to match to be better on the eyes.

Thanks
S

I guess what I am asking is how to access System>Preferences>Appearance>Fonts as root.

---

### Post by jordanmthomas on 2007-11-22
run this:
```
gksudo gnome-appearance-properties
```
or 
```
gksudo gnome-font-properties
``` if you aren't running gnome 2.20
It will tell you gnome-settings-daemon couldn't be started or something.  Ignore it, and change your fonts as you please.

---

### Post by shuttleworthwannabe on 2007-11-22
You are a star! Thanks a million!

Now I am almost on Cloud-9!

---

### Post by TeaSwigger on 2007-11-22
> **shuttleworthwannabe said:**
> You are a star! Thanks a million!

Now I am almost on Cloud-9!

Why what's got you down here on Cloud-8? O:)

---

### Post by shuttleworthwannabe on 2007-11-22
Good one--but [this issue]("http://ubuntuforums.org/showthread.php?t=619976") is still pending, then I will surely leave Cloud-8...mmm!

---

