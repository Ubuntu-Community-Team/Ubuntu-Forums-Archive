---
title: "Make won't make"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by sabresong on 2006-12-07
Hello.

My fiancee and I have very recently switched to Linux, and chose Ubuntu for various reasons.  We've figured out the Synaptic Package Manager, but now she is trying to install something that isn't available throught Synaptic, and is only available in source.

We got as far as ./configure, which went well enough after we figured out that we needed gcc.  But when it came to the make command, we were told that make isn't a recognized command. Is there something we're missing here?

---

### Post by 23meg on 2006-12-07
```
sudo apt-get install build-essential
```will install make, gcc and other required tools.

---

### Post by sabresong on 2006-12-07
Thank you very much, both for the help, and the amazingly fast response.

---

### Post by 23meg on 2006-12-07
You're welcome. If you do a forum search before asking questions you can usually get to answers even faster.

---

