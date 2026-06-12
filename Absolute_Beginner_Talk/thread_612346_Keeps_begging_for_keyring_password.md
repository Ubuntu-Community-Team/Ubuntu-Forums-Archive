---
title: "Keeps begging for keyring password"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by frank26080115 on 2007-11-13
My laptop's battery ran out while it was running, and now Ubuntu keeps asking me for a keyring password at every startup. How do I disable this?

See screenshot attached.

---

### Post by flickerfly on 2007-11-14
There might be something in your session about gnome-keyring-manager. You could remove that.

---

### Post by Inxsible on 2007-11-14
It is asking you to create a keyring password that will store the passwords of the multiple wireless networks that you may connect to. That way, instead of remembering 10 different passwords for 10 networks (that you connect to) you can remember only 1 password for the keyring manager and it will pick up the network password from the keyring manager.

If you don't want to create a password, then simply click Deny.

---

