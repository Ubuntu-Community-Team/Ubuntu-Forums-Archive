---
title: "[SOLVED] Whats this???"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by LizardKing73 on 2007-11-18
I was running an update when I got this error message.

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

So what the heck?
How do I fix it?

---

### Post by tyggna1 on 2007-11-18
just click on your own link, download the package, assign executable permissions to it (right click on the file and select properties, under the permissions tab) and then run it.

For a more perminant fix, you need to type in this on the command line:```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

---

### Post by anandanbu on 2007-11-18
Try to get the key from the site where you added this link. It solves this problem ;)

---

### Post by LizardKing73 on 2007-11-18
I've said it before and I'm sure I'll be saying THOUSANDS more times but Y'ALL ROCK :guitar:
Thanks

---

