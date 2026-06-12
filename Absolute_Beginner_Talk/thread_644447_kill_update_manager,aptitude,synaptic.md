---
title: "kill update manager,aptitude,synaptic????"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Staticboy44 on 2007-12-18
Im trying to Install the game OpenLieroX beta 3 from a DEB file and i get an error saying i need to quit Update Manager, Aptitude, or Synaptic before it can run the installation.

Can anyone help with this? What are the process-names of those programs. so that i may kill them?:confused:

Im using Kubuntu Gutsy 7.10 by the way.

---

### Post by CatKiller on 2007-12-19
If you've definitely not got one of those running (they're all graphical except for aptitude, and that only locks when it's really doing something), you probably need to delete the lock file. The location of that file depends on which part it was doing when it made the lock, but it might be at either **/var/cache/apt/lock** or **/var/lib/dpkg/lock**.

---

### Post by Staticboy44 on 2007-12-19
ok i found a lock file in Dpkg but not in apt folder. I deleted. So now what do i do? Restart?

---

### Post by CatKiller on 2007-12-19
Just try again.

---

