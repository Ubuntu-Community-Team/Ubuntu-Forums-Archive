---
title: "Synaptic &amp; add/remove not working"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by AbsolutMayhem on 2007-07-06
Extreme newbie to linux.

I tried to add new repositories and I think I messed up. Now when I try to run synaptic and add/remove, I get the following (screenshot attached). How can I correct this?

I'm not sure how to attach the screen shot, so here's the error I get:

E: Malformed line 34 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read
Go to the repository dialog to correct the problem
E:_cache->open() failed, please report

---

### Post by greg_g on 2007-07-06
Go to Applications -> Accessories -> Terminal

type this command
```

cat /etc/apt/sources.list

```

Paste the result here.  I think there is just a messed up line in that file, and we can probably find it pretty quickly.

---

### Post by Raineer on 2007-07-06
lol... I just did that to myself not 30 minutes ago

It will happen when you add a URL to the end of your sources.list but forget to put "fiesty" and a category after the URL :)

---

