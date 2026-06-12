---
title: "Wine doors..."
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by nikoPSK on 2007-09-22
Wine doors is giving me stupidness. I try to install a prgrom eg: half life 2 then it gets stuck saying executing installer. Also I can't seem to un-install anything. It gets stuck on that as well... I don't know how to install the earlier version. (since all my efforts have failed with the newest) After i Cd to the directory then what?

Heres the instructions (i've tried but wine-doors doesn't appear anywhere.)

INSTALL
-------

To install wine-doors perform the following operations

python setup.py install 

The two options --prefix=/prefix/path and --config=/config/path are supported and should be
identical on install/uninstall the defaults are /usr and /etc

This Is what I get once I've done that:

```
niko@ubuntu:~$ cd wine-doors-0.1pre1
niko@ubuntu:~/wine-doors-0.1pre1$ python setup.py install
Compressing and installing pack files
  ** Base Repo
  ** Global Repo
  ** Games Repo
Symlinking executable
/home/niko/.local/share/wine-doors/src/winedoors.py
Creating initial preferences
niko@ubuntu:~/wine-doors-0.1pre1$ wine-doors-0.1pre1

```

:confused: It doesn't appear... And I've tried re-starting to see if that's what it requires but apparently not...

---

### Post by bodhi.zazen on 2007-09-22
Well, I have had problems with winedoors in that it is still in Alpha or pre-release. It is in rapid flux.

Last time I looked you started the application with ```
wine-doors
```

What problem are you having exactly and what is the error message ?

---

### Post by nikoPSK on 2007-09-22
In the latest version I was having problems installing. things "gets stuck" and un-installing things (crap, now I'm stuck with IE6 and Steam...) stuck as well. So I'm trying an older version. But I suppose I could just wait until it becomes more stable...:(

---

### Post by xkendrax on 2007-09-27
Hello, i got a problem about wine-doors, it seems that i can install programs but they wont run once i open them, i also cant uninstall those programs, they stay in the system even after removing wine and wine-doors, what can i do to remove those programs?

---

### Post by ayenack on 2007-09-27
An alternative alternative if you get what I mean is [ReactOS]("http://www.reactos.org/en/index.html"). It's not MS Windows but runs MS compatible programs and games. It's a free open source OS.

ayenack.

---

### Post by nikoPSK on 2007-09-27
Thanks!:KS I will give it a shot. If that doesn't work I'll report my problems.:)

---

### Post by crapgar on 2007-12-31
I am basically having the same problem. Everything was running smoothly until I discovered that you can't switch disks during the HL2 installation. I tried to uninstall steam and hl2 but I cant.

---

