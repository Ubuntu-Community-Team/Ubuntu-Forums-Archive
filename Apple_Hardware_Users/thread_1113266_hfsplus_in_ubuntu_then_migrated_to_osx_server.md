---
title: "hfsplus in ubuntu then migrated to osx server?"
date: 2009-04-01
forum: Apple Hardware Users
---

### Post by Apocrathia on 2009-04-01
okay so i want to get some verification before I actually try this, but it seems like it will work. I have an ubuntu 8.10 server right now, I am planning to get a mac mini and running osx server in the future. right now, i have a raid cage in my server that has a few hard drives in it, but not raided. I am planning on getting a drobo shortly, and I am thinking that I am going to format it as HFS+, so that my ubuntu box can use it, but then it will be painless to move to the new mac mini.
will this be possible?

---

### Post by cyberdork33 on 2009-04-02
> **Apocrathia said:**
> okay so i want to get some verification before I actually try this, but it seems like it will work. I have an ubuntu 8.10 server right now, I am planning to get a mac mini and running osx server in the future. right now, i have a raid cage in my server that has a few hard drives in it, but not raided. I am planning on getting a drobo shortly, and I am thinking that I am going to format it as HFS+, so that my ubuntu box can use it, but then it will be painless to move to the new mac mini.
will this be possible?
yes. the downside is that HFS+ is not writable from linux unless you disable journaling.

---

