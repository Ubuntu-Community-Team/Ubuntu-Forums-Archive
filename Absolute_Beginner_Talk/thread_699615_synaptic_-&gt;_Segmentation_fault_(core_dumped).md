---
title: "synaptic -&gt; Segmentation fault (core dumped)"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by billgoldberg on 2008-02-17
So I can't open synaptic or add/remove nor can I use apt-get or aptitude.

They all say (in terminal) "Segmentation fault (core dumped)".

Yeah, this is a problem.

---

### Post by Jussi Kukkonen on 2008-02-17
Could try "sudo rm /var/cache/apt/*.bin". I've heard corrupt cache might do that.

You might want to save those files first -- if removing them works you could file a bug and the developers might find the files useful.

---

### Post by billgoldberg on 2008-02-18
That did the trick.

How would I submit a bug report?

---

### Post by Jussi Kukkonen on 2008-02-18
I think it's this one:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/16467](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/16467)

No-one is asking for the *.bin files there so maybe they aren't useful...

---

