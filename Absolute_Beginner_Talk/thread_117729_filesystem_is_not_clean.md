---
title: "filesystem is not clean"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by kasemodz on 2006-01-15
alright I got this error, when I booted my ubuntu. 
> This filesystem is not clean.
replaying journal
starting hotplug subsystem...                [18..8211]: 2 transactions replayed [ok]

Does this mean I'll have to reinstall ubuntu?

---

### Post by dueY on 2006-01-15
I think I've gotten that before.  I believe it checks itself every twenty mounts or so.  It usually finds some little thing wrong with mine and fixes it.  Mine still works fine.

---

### Post by Vinci71 on 2006-01-15
[QUOTE=dueY]I think I've gotten that before.  I believe it checks itself every twenty mounts or so.  It usually finds some little thing wrong with mine and fixes it.  Mine still works fine.[/QUOTE]

I think that a check is forced if some inconsistency is found at startup. Otherwise it forces the check every n mounts (where n can be configured). I left it at 30 as default, but it usually don't find anything wrong. Otherwise, even if it is not the 30th mount, if I had some kind of failure during shutdown, it is possible to find errors at boot.

---

