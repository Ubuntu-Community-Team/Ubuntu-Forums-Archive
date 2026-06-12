---
title: "Updates Upgrades"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by bkeithly on 2007-01-18
Does anyone know how to keep nvidia drivers and ndiswrapper from getting overwritten when upgrades are performed?


2 times now I have done udates and I lost my networking and video settings....  Basically ndiswrapper stopped working, and nvidia drivers broke.

I have a scripted backup process that I can easily restore from (well it takes some time to copy the backups over and un tar them).  Yet I would prefer to not have to do this.

Ideas anyone???

---

### Post by sbassett on 2007-01-19
There is a way to keep them from being updated. However, it appears that these would only  be updated once a kernel update came out. Which puts you in a bit of a bind.

As far as the settings are concerned, these SHOULD be kept automatically when being updated, with the default conf being saved with a .suffix (I can't remember exactly how ubuntu names them, but RHEL names theirs .rpmnew).

Are you stating that all of your changes to the defaults are being overwritten? If so, this should not be.

---

### Post by schwascore on 2007-01-19
Do they break when you upgrade kernel versions or are they being overwritten by newer/different versions from the repositories?

---

