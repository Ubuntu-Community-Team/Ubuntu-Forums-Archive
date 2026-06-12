---
title: "Questions about Ubuntu"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by kunalbelnekar on 2007-01-25
Hi !

I was reading some online documentation about how Linux in general works. It talks about init reading the /etc/inittab to find out which services should be run and at which run levels.Also talks about the /etc/getty and the /etc/ttys that are read in order to start communication with terminals.

My biggest problem here is that I cannot find the /etc/inittab here on Ubuntu.Nor can I find the /etc/ttys or the /etc/getty.Are they in some other directory? I did a search in / for inittab and it still did not return anything.
Am I missing something here ? Im running Ubuntu 4.1.1-13ubuntu5.

Thanks !:confused:

---

### Post by userundefine on 2007-01-25
Some distributions put certain files in different places.  Most of what you're looking for is in /etc/event.d/.  This has to do with Edgy using Upstart for initialize services.  However, in general, the standard Linux root structure is followed.

---

### Post by kunalbelnekar on 2007-01-25
Thanks !

However I still dont see inittab in it.Which file does init read ?

---

### Post by userundefine on 2007-01-25
Well, there is no standard 'inittab' anymore, as such.  But things normally contained in inittab, such as runlevels and ttys, are now in that directory.

---

### Post by kunalbelnekar on 2007-01-25
k. Thanks !!!

---

