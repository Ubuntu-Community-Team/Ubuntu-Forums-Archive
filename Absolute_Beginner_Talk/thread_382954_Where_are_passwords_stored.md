---
title: "Where are passwords stored?"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Shack_ on 2007-03-12
I was wondering, where are passwords stored on Linux? Are they stored in an invisible file, and if they are, how would I access them? Also, are they encrypted? Are they stored as hash files? Can you read the contents of these files from a boot menu? Information on this subject would be much appreciated.

Also, are there package files for Linux I can download that will decrypt hash files, similar to John the Ripper?

---

### Post by taurus on 2007-03-12
Your passwd is stored in /etc/shadow and it is encrypted so you can't just look at it.

---

### Post by Shack_ on 2007-03-12
Okay. So, are there programs for Linux to decrypt hash files?

---

