---
title: "Frets on Fire problem"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by dnns123 on 2007-11-11
I get this when I type it in the terminal

> 
dnns@ubuntu:~$ fretsonfire
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 166, in __init__
    self.svg = SvgContext(geometry)
  File "/usr/share/games/fretsonfire/game/Svg.py", line 78, in __init__
    self.setGeometry(geometry)
  File "/usr/share/games/fretsonfire/game/Svg.py", line 91, in setGeometry
    geometry[2], geometry[3])
  File "/usr/share/games/fretsonfire/game/DummyAmanith.py", line 42, in SetViewport
    glViewport(x, y, w, h)
ctypes.ArgumentError: argument 3: <type 'exceptions.TypeError'>: wrong type


The screen goes black and back to the desktop.

---

### Post by Daveth on 2007-11-11
did you download this from the gutsy repository where I believe there is a copy? Or from sourceforge?

---

### Post by dno on 2007-11-11
I have the same problem and I downloaded it through the repositories.

---

### Post by mishkind on 2007-12-17
same problem. I have an 8600 GTS if that can help anybody debug things.

---

### Post by macogw on 2007-12-17
It's in Gutsy's repo now?

I installed it from Debian's repo, and it works fine.  Oddly, they're the same package version so I don't know why the one in the Ubuntu repo doesn't work for you guys.

---

### Post by spodesabode on 2008-03-02
I've got the same problem. I'm running dual displays on nvidia. Tried turning off Compiz and didn't make a difference.

---

### Post by stmiller on 2008-03-02
Details of this bug are on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/fretsonfire/+bug/136844](https://bugs.launchpad.net/ubuntu/+source/fretsonfire/+bug/136844)

Unfortunately looks like Hardy does not include the recent version of fretsonfire with the fix:

[http://packages.ubuntu.com/search?keywords=fretsonfire&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=fretsonfire&searchon=names&suite=all&section=all)

:(

--

EDIT: You can download the latest version directly from the Frets On Fire website:

[http://fretsonfire.sourceforge.net/](http://fretsonfire.sourceforge.net/)

Then extract the tarball and play right from that folder:
```

$ tar xvzf FretsOnFire-1.2.512-linux.tar.gz

$ cd FretsOnFire

$ ./FretsOnFire

```

---

### Post by monoufo on 2008-03-20
but no one uses that version.  None of the mods work.  vanilla frets on fire isn't that great, we need it with the good mods.

---

