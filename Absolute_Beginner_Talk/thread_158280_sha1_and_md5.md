---
title: "sha1 and md5"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by Stuperfied on 2006-04-10
I just downloaded TeamSpeak for linux from a 3rd party source because the link on the goteamspeak.com site was broken, now I need to check it against the sha1 on the goteamspeak.com site to see if it is legit before I install it, how do I do that?

---

### Post by paulipe on 2006-04-10
"md5sum <filename>" and check that the output matches the same as the md5sum on the website.
Or you can do "sha1sum <filename>" and check on the website that the sums match

---

### Post by Stuperfied on 2006-04-11
Thanks, it worked like a charm.

---

