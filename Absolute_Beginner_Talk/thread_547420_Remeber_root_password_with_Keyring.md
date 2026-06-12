---
title: "Remeber root password with Keyring"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by mevets on 2007-09-10
I recently loaded up Debian Etch on my laptop and although I eventually dumped it, there were somethings that I really liked. One of those things is that it would remember my root password with the keyring. Is there a way to configure Ubuntu to remember my root password with the keyring?

---

### Post by mcduck on 2007-09-10
> **mevets said:**
> I recently loaded up Debian Etch on my laptop and although I eventually dumped it, there were somethings that I really liked. One of those things is that it would remember my root password with the keyring. Is there a way to configure Ubuntu to remember my root password with the keyring?

You should not even need a separate root password with Ubuntu :D

---

### Post by mevets on 2007-09-10
Huh? I am aware that I only have one root password. I was under the impression that the keyring would remember the root password for many applications and last longer than just manually typing it in everytime Im prompted. I may be wrong though, will the keyring remember my root password and supply it to any apps without bothering more than just the once when it first asked me for the password to the keyring?

---

### Post by BrendanM on 2007-09-10
I think it should actually remember your password for a while.
By default, Ubuntu sets the "root" account to a random password, and then just has you use your user password with "sudo" to do system maintenance tasks. I think the idea is to not confuse users with the idea of root. They just have to type in their password like on OS X.

---

