---
title: "update manager not working??"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by sneeks on 2008-03-20
have just installed a gutsy on an old pc,but did not have net connection when i was installing.
so by-passed it as was asked and now when i try to update the system it says all is well.
have tried to do the sudo aptitude route bit to no avail.
i can not also get the add/remove programs list to update or the package manager.
any help would be good chaps.
sneeks

---

### Post by munkyeetr on 2008-03-20
A few questions...

> **sneeks said:**
> ...now when i try to update the system it says all is well...

What do you mean? It tells you all packages are up to date? Please clarify.
Are you able to connect to the Internet and browse? Is it a network issue, or a Package Manager issue?

---

### Post by sneeks on 2008-03-20
ok chaps.solved it,the check was on use cd/dvd and not the net.
it was just rying to update from the disk only,so un-checked the box and all is well,and checked the other update boxes..
sneeks

---

### Post by binarymutant on 2008-03-20
check out [https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu") you might have some luck after reading that. To access the online repositories you'll have to get a net connection, however, you can install the programs that came with the installation cd/dvd.

---

### Post by jimv on 2008-03-20
If you had looked at your /etc/apt/sources.list file, you would have noticed that all of the sources except the CD were commented out.  For some reason that happens when you install without a network connection.

---

