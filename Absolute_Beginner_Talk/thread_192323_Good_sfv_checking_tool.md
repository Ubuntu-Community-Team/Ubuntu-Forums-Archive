---
title: "Good sfv checking tool"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by hikitsu4 on 2006-06-08
Hello i was wondering if there are any simple/good SFV checking tool that is GUI based and you can get with synaptic.

---

### Post by hikitsu4 on 2006-06-09
Anyone?

---

### Post by hw-tph on 2006-06-09
GUI is a tad overkill for sfv checking. cksfv is small, straightforward and easy to use in scripts, so that's what I use.

sfv is extremely weak though, so don't rely on it. Also, md5 sums are vulnerable too so using something strong like the OpenSSL SHA1 algorith would probably be a lot wiser (use **openssl sha1 <filenames>** to generate a digest).

Håkan

---

