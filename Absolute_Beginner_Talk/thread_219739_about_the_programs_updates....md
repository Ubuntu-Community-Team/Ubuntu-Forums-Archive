---
title: "about the programs updates..."
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-07-20
I heared that I don't need to worry about it cuz it comes with ubuntu updates, but I don't see it.
I have firefox version 1.5.0.4...is it updates ???
and I started to use blender3d - I had the older version , and on blender's official site the next version was already published - but I didn't see it in the updates (not on ubuntu updates and not in synoptic manager).
why ?
do I really need to search for all the updates myself ???
there are tons of programs.

---

### Post by qdvubun on 2006-07-20
It will be in the Sypnatic package manager if it founnd an update, you can click on the Status button on the bottom left and it will have an update option for softwares.

---

### Post by MaximB on 2006-07-20
the problem is it didn't find all the upgrades/updates

---

### Post by mattisking on 2006-07-20
Just because a website announces a new version of a program, doesn't make it immediately available through Synaptic/aptitude/apt-get. Once a program already available on the Ubuntu repositories gets updated, it takes a while sometimes for the new/updated package to be created for Ubuntu. At that point, you will eventually be notified by the update-manager that the update(s) are available.

Packaging is difficult because in general, packages (particularly application packages) contain dependent packages. While all application and library developers do their best not to break compatibility from one major release to another, sometimes there is no way to avoid this. So, when a major release of an application comes out, a decent amount of testing is necessary to determine what other library packages might need updating and what the ramifications are (if any) to other applications that have some of the same dependencies.

Often times you'll find that major application updates aren't packaged for lower versions of any Linux Distribution. This is probably not AS true with Dapper which is promising 5 years of support. However, it might be longer than normal because Dapper has been released and Edgy is being developed. Because of people that don't like to wait, another effort has been created called "backports". Backports (which is a repository you can enable in your /etc/apt/sources.list file) provide newer applications developed in the distribution being developed (in this case, Edgy Eft) to be "back-ported" to your distribution version (which is hopefully dapper). Backports is a WONDERFUL effort. You should try enabling that. This might greatly increase the speed at which your new application version becomes available to you.

The next option, of course, is to download the source and build it yourself. That, however, is a larger topic that I won't delve into unless you need to.

---

### Post by rhomp2002 on 2006-08-03
I reloaded the Breezy version of Ubuntu.  I got the indicator to do an update to Dapper and clicked it to do the install.  It did the updates and then said that the Ubuntu-base was missing now and to inform the forums of the bug.

---

### Post by MaximB on 2006-08-04
send it with the "bug report tool"
this is very importent

---

