---
title: "emc2 installation failure"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by TonyFromOR on 2006-08-26
Hi guys,  I'm totally new to ubuntu, so please bear with me.  I recorded the following errors while trying to install emc2: If anyone has any suggestions, I would very much appreciate any help!!!](*,) 

Err [http://dsplabs.cs.upt.ro](http://dsplabs.cs.upt.ro) dapper Release.gpg
  Temporary failure resolving 'dsplabs.cs.upt.ro'
Fetched 3B in 20s (0B/s)
Failed to fetch [http://dsplabs.cs.upt.ro/emc2/dists/dapper/Release.gpg](http://dsplabs.cs.upt.ro/emc2/dists/dapper/Release.gpg)  Temporary failure resolving 'dsplabs.cs.upt.ro'
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package emc2-axis

---

### Post by Schalken on 2006-08-26
It's trying to get stuff from dsplabs.cs.upt.ro, but it looks like the site is down. (try putting the address in your browser, nothing comes up) Tell me, what's emc2?

---

### Post by Brad wilkinson on 2006-08-27
Enhanced machine controller 2.

It's an open-source CAM (computer aided manufacturing) program. You can set it up to run mills, lathes and other computer controlled machines.

see also linuxcnc.org

---

