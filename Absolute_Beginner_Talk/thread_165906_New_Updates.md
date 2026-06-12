---
title: "New Updates"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by dunomous on 2006-04-25
Two new updates, libsasl and libsasl2 are listed as not being authenticated. Obviously this can just be a small precaution as I'm sure it's fine; however, I'd rather check first. These forums can serve as n00b insurance time and time again.

---

### Post by Jagot on 2006-04-25
These are both from the universe repository which is not officially supported by Canonical, which is probably why it's saying they're not authenticated.  You should be fine to go ahead and install them.

More information about the Universe repository can be found here:

[http://www.ubuntu.com/ubuntu/components](http://www.ubuntu.com/ubuntu/components)

---

### Post by dunomous on 2006-04-25
ah, thank you so much!

---

### Post by nanotube on 2006-04-25
[QUOTE=dunomous]Two new updates, libsasl and libsasl2 are listed as not being authenticated. Obviously this can just be a small precaution as I'm sure it's fine; however, I'd rather check first. These forums can serve as n00b insurance time and time again.[/QUOTE]
hmm, when i installed those updates they were authenticated just fine...
oh and by the way, Jagot, you are not correct - libsasl2 is in the official repository, not in universe.

---

### Post by Jagot on 2006-04-25
[QUOTE=nanotube]hmm, when i installed those updates they were authenticated just fine...
oh and by the way, Jagot, you are not correct - libsasl2 is in the official repository, not in universe.[/QUOTE]

Aha, yep, you're correct.  Looking at some metapackage in Hoary there :???:

---

### Post by towsonu2003 on 2006-04-25
[QUOTE=Jagot]These are both from the universe repository which is not officially supported by Canonical, which is probably why it's saying they're not authenticated. [/QUOTE]
as long as it's a proper repo, doesn't matter if it's official or not. It should be marked as authenticated (that is my experience so far). 

When that happens to me, I usually do
```

sudo apt-get clean #cleans the cache
sudo apt-get update
sudo apt-get upgrade

```and it gets fixed by itself.

---

