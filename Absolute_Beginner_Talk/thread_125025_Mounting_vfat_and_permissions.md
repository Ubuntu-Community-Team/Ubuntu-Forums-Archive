---
title: "Mounting vfat and permissions"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by mathfreq on 2006-02-02
I've got a second hard drive on my machine with a single partition formatted as fat32. I want to give myself readwrite permissions on the drive, but I also want it to be read-only for a second account on my computer. I've tried playing around with groups, but I can't figure out how to change group ownership for this mount. If anyone could teach me how to manage groups on a fat32 mount or point out another solution to my problem, I'd greatly appreciate it.

---

### Post by aysiu on 2006-02-02
FAT32 doesn't support permissions, as far as I know, not the kind you're talking about (per user).

---

### Post by towsonu2003 on 2006-02-02
@aysiu: can s/he give a umask=xxxx option in fstab to vfat for the permissions? I am extremely ignorant about umask (can't understand the numbers) so I couldn't suggest anything.

---

### Post by mathfreq on 2006-02-02
I've played around with umask options. I'm currently mounting it with umask=000 just to give myself write permissions, but couldn't I do something with groups so that I can mount it as umask=002 instead?

---

### Post by towsonu2003 on 2006-02-02
[QUOTE=mathfreq]I've played around with umask options. I'm currently mounting it with umask=000 just to give myself write permissions, but couldn't I do something with groups so that I can mount it as umask=002 instead?[/QUOTE]
try 0002. it's supposed to give full privileges to you and read/execute (for directories) to anything else according to my linux guide ("linux pocket guide"). [sidenote:]if you wanna get more strict, don't use the user option (which makes it mountable by all). also give noauto and nouser options so that *you* can mount it with sudo only after boot whenevr you want with mount.[/sidenote]  but I'm not sure wether umask 0002 would work out in a mounted fylesystem. I'm pretty ignorant in umask numbers.

you might wanna create a temporary user and test this after a log out (log yourself out, log temp user in, test access) as well as after a boot (login as temp user and test access)?

---

