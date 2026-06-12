---
title: "[SOLVED] Error while installing Dctc."
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by rhc on 2008-01-11
> Press return to resume configuration (CTRL-C to abort).
================================================================================
checking for libgcrypt-config... yes
checking gcrypt version... 1.2.4
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... yes
checking db.h usability... no
checking db.h presence... no
checking for db.h... no
configure: error: BerkeleyDB include required.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

I found something from Synaptic,db4.6-util(berkeley v4.6 database utilities),but i didnt solve the problem.
Any idea?

---

### Post by nikoPSK on 2008-01-11
> **rhc said:**
> I found something from Synaptic,db4.6-util(berkeley v4.6 database utilities),but i didnt solve the problem.
Any idea?

Happens on some packages to me. I usually find adding dependacies helps. Did you run ./configure before make? Have you checked the README? Try running make clean to start over. 

Best,
nikoPSK

---

### Post by rhc on 2008-01-12
I installed LinuxDC++ instead.
Good program.
Thanks anyway.

---

### Post by nikoPSK on 2008-01-12
No problem, could you please mark this thread as "SOLVED" by going to the top of the page, then thread tools -> mark this thread as solved. :)

Best,
nikoPSK

---

