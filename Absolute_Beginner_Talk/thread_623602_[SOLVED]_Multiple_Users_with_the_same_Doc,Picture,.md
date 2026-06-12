---
title: "[SOLVED] Multiple Users with the same Doc,Picture, and Music Folders?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Tdukes on 2007-11-26
Is this possible?  I want to share our Document, picutures, and music folders but still have user settings different.

---

### Post by jordanmthomas on 2007-11-26
You can put these folders somewhere else (anywhere you want, really) and make symbolic links for each user.

For example, say you decided to put your pictures folder in /share/pictures.  In each user's account run this:
```
ln -s /share/pictures pictures
```
Then, there will appear to be a pictures directory there.  In reality, it's just a "shortcut" to /share/pictures.

Do you see what I'm getting at?

---

### Post by Tdukes on 2007-11-26
> **jordanmthomas said:**
> You can put these folders somewhere else (anywhere you want, really) and make symbolic links for each user.

For example, say you decided to put your pictures folder in /share/pictures.  In each user's account run this:
```
ln -s /share/pictures pictures
```
Then, there will appear to be a pictures directory there.  In reality, it's just a "shortcut" to /share/pictures.

Do you see what I'm getting at?

I see what your saying.  My only issue with that is under the "places" tab you will see Pics, Docs, and Music that arent really used for anything at all

---

### Post by jordanmthomas on 2007-11-26
My nautilus doesn't have these to begin with, but I believe I know what you're saying.
You can right click on the old, meaningless ones and remove them.  Then, drag your new, wanted, ones over onto the places bar like what I did in this screenshot (I put a src and a sprites folder in there)

---

### Post by Tdukes on 2007-11-26
> **jordanmthomas said:**
> My nautilus doesn't have these to begin with, but I believe I know what you're saying.
You can right click on the old, meaningless ones and remove them.  Then, drag your new, wanted, ones over onto the places bar like what I did in this screenshot (I put a src and a sprites folder in there)

Ok, I will just drag the shared folders over there then. Thanks all.  solvage

---

