---
title: "Crossover Office Installation Assistance"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-10-22
I get stopped when installing the beta trial mode of Crossover. When running
 "sudo sh install-crossover-standard-prerelease-6.0.0beta2.sh" it says 
```
"The '/home/shane' directory does not belong to you.
Point $HOME to your home directory and try again."
```

any ideas?

---

### Post by jordanmthomas on 2006-10-22
Install it as yourself.
ie
```
sh install-crossover-standard-prerelease-6.0.0beta2.sh
```
It will install it in your home directory.

Root doesn't own your home directory, which is why you were getting that error.

---

### Post by shanepardue on 2006-10-22
DUH! ha, silly me. Thanks for the assistance!!

---

### Post by jordanmthomas on 2006-10-22
I dunno...I wouldn't say it's worthy of a DUH.  Generally, you need root privileges to install stuff.

---

### Post by shanepardue on 2006-10-22
Ha, thanks for the consolation!

---

