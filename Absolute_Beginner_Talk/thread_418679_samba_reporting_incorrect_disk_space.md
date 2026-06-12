---
title: "samba reporting incorrect disk space"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by dbansal on 2007-04-22
Hello,

I have mounted my external fat32 harddrive and i have shared it publicly with samba with browsability turned off ( i could not get it to work when i tried to make it so only one user has access to it.) 

The harddrive was split into two partitions. I am trying to map both partitions with windows. However, when i map it it says that both drives only have 4.88 gb of space. Also, when i add something to one drive, the space in both drives diminishes.

This is a 250 gb harddrive. Any ideas?

---

### Post by dbansal on 2007-04-22
odd, but i ran sudo mount -a and it worked!

---

