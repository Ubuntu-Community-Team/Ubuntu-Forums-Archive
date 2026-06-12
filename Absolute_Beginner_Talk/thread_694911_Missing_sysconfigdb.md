---
title: "Missing sysconfigdb?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by dwight_lillie on 2008-02-12
I'm installing Oracle 9i.  In the pre-install instructions, a new entry is to be created in /etc/sysconfigtab:

vm:    new_wire_method = 0

Unfortunately this file seems to be non-existent.  Some googling around indicates that this file is maintained by /sbin/sysconfigdb.  This program likewise is non-existent.  Searching in synaptic package manager was of help.

Thoughts?

thanks, -Dwight

---

### Post by Presto123 on 2008-02-13
Try this (It could just be a mis-typed command and not really missing):

```
gksudo gedit etc/sysconfigtab

```

Also, you could be searching for a hidden file. Hit CTRL+H to find hidden files/folders when searching.

---

