---
title: "No tty sessions"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-12-09
Hey all, 
I just installed 6.06 on my laptop and everyhting is fine except I am unable to ctrl+alt+f1,f2 etc
The screen just goes black and I see nothing
I am able to ctrl+alt+f7 back into my x session though...

Please help.

---

### Post by Wim Sturkenboom on 2006-12-09
Not sure. There might be a couple of reasons.
Check the following in /etc/inittab (below from a default dapper install):
```
# The default runlevel.
id:[COLOR="Red"]2[/COLOR]:initdefault:

```This shows which runlevel your system is using (here it's 2). Next check a little further in the file
```
1:[COLOR="Red"]2345[/COLOR]:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

```The first line shows that in runlevels 2,3,4 and 5 tty1 is available while the other ttys (2..6) are only available in runlevels 2 and 3.

If your config seems to be correct, there might be a video driver issue. I'm not sure if I can help with that.

---

### Post by charles.g.moore on 2006-12-09
here is a snippet of the file...

id:2:initdefault:

1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

I think it looks right, do you agree???

---

### Post by riven0 on 2006-12-09
Did you notice this problem after you installed the xserver updates from canonical? I'm asking because I'm currently having a problem accessing my tty sessions. In my case, though, hitting alt+ctr+f1, etc doesn't do anything.

---

### Post by charles.g.moore on 2006-12-09
you know , i just did a fresh install and I remember seeing the tty login screen before I updated my nvidia driver, that was just before i did an upgrade (about 200pckgs) so it probably did have something to do with the x update...

---

### Post by Wim Sturkenboom on 2006-12-09
Same as mine; so the problem is not there.

---

### Post by charles.g.moore on 2006-12-09
any ideas as far as what may be causing the problem?
i have a feeling it has to do with X.

---

### Post by riven0 on 2006-12-09
I'm still trying to figure this one out. Doesn't look like we're the [only ones though]("http://www.ubuntuforums.org/showthread.php?t=300061").

---

### Post by charles.g.moore on 2006-12-10
so has anyone found anything yet?
i need my terminal sessions...

---

