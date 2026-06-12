---
title: "HELP!!! Mounted read-only filesystem"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by AngryMallard on 2007-07-29
HELP!

I tried to mount an external hard drive and I did something really wrong. Now when my computer boots it does a file system check, gets to about 30%, then mounts the filesystem in read-only mode. I have a command prompt with root access but it won't let me do anything else.

---

### Post by splintercellguy on 2007-07-29
Type fsck at the command prompt?

---

### Post by AngryMallard on 2007-07-29
About how long should this take? It's either crashing or it's taking a super long time.

---

### Post by splintercellguy on 2007-07-29
If it's a large partition it should take a bit of time. fsck is repairing the filesystem, you should be getting prompts.

---

### Post by AngryMallard on 2007-07-29
Nope. fsck did not fix the problem.

---

### Post by AngryMallard on 2007-07-29
OK WAIT! It did fix it. Thanks!

---

