---
title: "[SOLVED] LUKS questions"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by WorldTripping on 2007-06-05
I'm in the process of wiping and formatting an external HDD.

It will be encrypted using LUKS.

My question is: If I re-install a different Ubuntu kernel (and DM Crypt), will I still have access to the encrypted external volumes.

(Aplologies in advance if this is a stupid question).

---

### Post by Stephen Howard on 2007-06-05
Not a stupid question at all.  The answer is that the luks partitions will happily survive.  I recommend that you don't encrypt everything, just you data directories  - it makes life easier if things go wrong.

---

### Post by WorldTripping on 2007-06-05
Thanks for the reply.

I was actually going to go the whole way and encrypt the entire file system.

(After encrypting the external data directories.)

You've now given me something to think about.

Cheers.

---

