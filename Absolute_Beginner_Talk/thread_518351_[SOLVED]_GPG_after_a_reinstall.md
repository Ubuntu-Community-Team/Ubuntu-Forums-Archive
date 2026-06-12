---
title: "[SOLVED] GPG after a reinstall"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by palintheus on 2007-08-05
On my original install I generated a gpg key and used it to sign the CoC, I have since had to reinstall and my gpg is not on my computer and I do not know what to do to a) retrieve my key and get it on my computer, or b) revoke/delete that signature and start over.

---

### Post by apswartz on 2007-08-05
If you didn't back up the key you are out of luck. If you didn't create and backup a revocation certificate you can't do that either.

---

### Post by palintheus on 2007-08-05
Ok, so, where does that leave me? Do I do anything or just generate a new key, and if so, what can I do to prevent this in the future?

---

### Post by apswartz on 2007-08-05
Yes, you will have to create a new key. I would also create a revocation certificate at the same time. Then back it up. I would recommend that you periodically backup you ~/.gnupg directory to cd and lock it up someplace safe.

---

### Post by palintheus on 2007-08-05
Is it a bad thing that I cannot revoke my first key?

---

### Post by apswartz on 2007-08-05
Not bad. Many of us still have an old unrevoked key on the keyserver. ;-) I once did the EXACT same thing you did.

---

### Post by palintheus on 2007-08-05
Thanks for your help and info.

---

