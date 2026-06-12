---
title: "file mode with a &quot;+&quot;"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Ephilei on 2008-03-10
what does the + mean in "drwxrwxrwx+" ?

---

### Post by Rocket2DMn on 2008-03-10
I think it is an extra set of permissions.  It seems that it represents ACL permissions - [http://en.wikipedia.org/wiki/Access_control_list](http://en.wikipedia.org/wiki/Access_control_list)
This might have more meaning in the sense of shared data, like on a public server or samba share.  Where are you seeing this?

---

### Post by Ephilei on 2008-03-22
I have an external HDD whose partition is shared at the root. I copied some files from the HDD to the home folder and it's having some access problems.

It's actually on a Mac, but it's still BASH so I thought it would all mean the same. I've seen in on Ubuntu too. File system on the external and internal drives are HFS+.

---

### Post by Ephilei on 2008-03-22
I still don't know what it means. But if I use mv or cp from the command line instead of the Finder (GUI file manager) the + no longer appears on the new copies and the file access problems stop.

---

