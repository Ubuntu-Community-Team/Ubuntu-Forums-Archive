---
title: "files list file for package `libtasn1-3' is missing final newline"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by sdgreen on 2007-04-23
Upgraded from Edgy to Feisty.

I keep on getting the following error - [COLOR="Red"] files list file for package `libtasn1-3' is missing final newline[/COLOR] = When attempting to either add programs via Synaptic, or otherwise removing a program.  Update actions also fail with the same problem. 

How to fix?

In appreciation for any help with this issue.

---

### Post by Cypher on 2007-04-23
Try
```

sudo apt-get -f install

```
and post back the results..

Regards

---

### Post by sdgreen on 2007-04-23
I seem to get the same error message.

[COLOR="Red"]**E: /var/cache/apt/archives/tzdata_2007e-0ubuntu0.7.04_all.deb: files list file for package `libtasn1-3' is missing final newline**[/COLOR]

---

### Post by Cypher on 2007-04-23
I don't have access to my Ubuntu machine right now, but can you do a "man apt-get" and "man dpkg" and look at how to clean out your cache. One you do so, the bad package will go away and hopefully take with it all it's problems..

Regards

---

