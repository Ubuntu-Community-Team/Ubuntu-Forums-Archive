---
title: "strange &quot;core&quot; file in home folder"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by bullon on 2006-11-08
there's a file in my home folder called "core.19065" it's large (116.3MB) and I have no idea where it came from or what it is... I want to get rid of it as it's kind of annoying, but I'm not sure if it's important or not.. 

p.s. it may be part of some torrent that i forgot about, but i don't think so...

---

### Post by sethmahoney on 2006-11-08
Well, its not a system file...

---

### Post by Seine on 2006-11-09
It's a core dump!

[http://en.wikipedia.org/wiki/Core_dump](http://en.wikipedia.org/wiki/Core_dump)

---

### Post by jordanmthomas on 2006-11-09
Chances are it is perfectly safe to remove (it's probably just a crashed program's dumped information) but a good way of checking if it's ok to remove is to just rename the file and see if everything still works.  If it does, it is safe to remove.  If things stop working, name the file back to what it was.

Though, personally, if it was in my home folder and I didn't know what it was I would just delete it after a quick inspection.

**beaten

---

### Post by bullon on 2006-11-09
thanks! renamed the file, I'll give it a day or two.

---

### Post by LLRNR on 2006-11-09
Hi bullon. I don't know wether it's safe or not to remove it, give it a try as jordanmthomas suggested, but I can tell you the "mechanism" behind it. Sometimes the OS sends certain signals to certain processes that you might have running. You can see the signals your OS "knows" by issuing ```
kill -l
``` (note : it won't "kill" anything, it will just display a list of the signals ; and also that "-l" is lowercase L, not digit 1).

Sometimes, when bad things happen, the OS realizes that and sends appropriate signals to those processes (it usually results in terminating them), and some of these signals also determine those **core dumps** used for debugging the error which was encountered.

Well don't ask me, I don't know *how* to read those, I only know *why* they're sometimes created.

Good luck !

LLRNR

---

### Post by kc8hr on 2006-11-09
Yep, you can delete it.

"Core dumps" are simply debugging files left over after a program crashes. The programmer who wrote the software might be interested in it, but it's pretty much useless for the rest of us.

---

### Post by Arndt on 2006-11-09
> **kc8hr said:**
> Yep, you can delete it.

"Core dumps" are simply debugging files left over after a program crashes. The programmer who wrote the software might be interested in it, but it's pretty much useless for the rest of us.

To find out where the core file comes from, do

```
$ file core.19065
```

Once you know that it comes from, say, the program 'gnasplut', and that it resides in /usr/local/bin, you can use the command

```
$ gdb /usr/local/bin/gnasplut core.19065
```

to inspect the data of the crash, perhaps see a stack backtrace of what the program was doing when it crashed.

If you're not planning to use it for debugging the crashing program, you can delete it.

You can tell the shell you don't want core dumps, by using

```
$ ulimit -c 0
```

The number 19065 is probably the pid of the process that crashed. There is a setting somewhere that says whether to generate plain "core" files always, or with names with the pid appended.

---

### Post by bullon on 2006-11-09
ok, i found out it was from swiftfox, which had crashed a few days ago... so I deleted it, thanks for all the help!:)

---

### Post by picpak on 2006-11-09
I solved this by removing apport (an automated crash reporter):

```
sudo update-rc.d -n -f apport remove
```

---

