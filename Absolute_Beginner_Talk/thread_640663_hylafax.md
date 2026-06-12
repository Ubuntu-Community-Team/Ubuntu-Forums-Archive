---
title: "hylafax"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by h4450 on 2007-12-14
I''m new to linux and am trying to get Hylafax to install. Followed the directions from Hylafax site.

sudo apt-get install hylafax-server hylafax-doc hylafax-client

getting follow message:

reading package lists...... Done
Building dependency tree
reading state information.....Done
E:couldn't ind package hylafax-server

---

### Post by jken146 on 2007-12-15
The package does exist (I just checked on packages.ubuntu.com); it is in the Universe reopisitory.  Go to System > Administration > Software Sources and make sure the box for Universe is ticked.  Then try to install it again.

---

