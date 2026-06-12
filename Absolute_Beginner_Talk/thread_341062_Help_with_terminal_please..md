---
title: "Help with terminal please."
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Phosphoric on 2007-01-18
Hi,

I had this query buried in a thread elsewhere in trying to debug a scanner problem (now fixed)

I was instructed to type in this code "$ export SANE_DEBUG_DLL=128 $ scanimage -L"

I had no luck.  Somebody suggested splitting up the code in to two which I did.  This is my terminal output:

ray@ubuntu:~$ $ export SANE_DEBUG_DLL=128
bash: $: command not found
ray@ubuntu:~$ $ scanimage -L
bash: $: command not found
ray@ubuntu:~$

It seems to me that I've got too many $s in the code.  I've googled the above code but haven't found anything.  Is the syntax correct?  If so, what am I missing/doing wrong?

Thanks :)

---

### Post by Stemp on 2007-01-18
don't type $ just scanimage -L (by example)
$ is just here to tell you it's a normal user terminal not a root one (with a #)

---

### Post by Phosphoric on 2007-01-18
That makes sense.

Thanks Stemp. :)

---

