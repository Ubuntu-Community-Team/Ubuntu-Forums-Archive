---
title: "upgrading to Xubuntu 710, backup question"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by zazen666 on 2008-01-09
Hi all,
I want to upgrade my xubuntu to 7.10 via the upgrade manager, upgrade button.

What do I need to back up before doing so, to be on the safe side?

---

### Post by hyper_ch on 2008-01-09
You should backup on a regular base... you never know what happens... tomorrow your harddisk could fail as an example...

So the answer is: yes!

---

### Post by zazen666 on 2008-01-09
actually, my question was how, not should I.

In other words, is there a way to do a full system back up, or is that overkill? Should I just copy important files to an external hard drive? Or is there some way to save the whole current state of my computer before attempting the update, in case it runs in to probelms so that I can revert?

---

### Post by hyper_ch on 2008-01-09
you could image your whole system, but then you'd need equally space somewhere else to do it. that would save the whole system in teh current state.

as for individual backups you need those folders:

/home
/etc
/var/www --> if apache is installed
/var/lib/mysql --> if you run mysql databases (but for those a mysql dump is preferred as backup method)

and besides that you have to know yourself what else you need to backup.

---

### Post by pebo on 2008-01-09
You could use [partimage]("http://www.partimage.org/Main_Page") from a live cd to mirror your partitions.

---

### Post by zazen666 on 2008-01-09
how do I image the whole system?

---

### Post by hyper_ch on 2008-01-09
> **zazen666 said:**
> how do I image the whole system?

by using this:

> **pebo said:**
> You could use [partimage]("http://www.partimage.org/Main_Page") from a live cd to mirror your partitions.

---

