---
title: "Bouncy the Hungry Rabbit/pygame problems?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Huzudra on 2008-01-03
when i launch it, i get a black screen and i have to force quit the window....any ideas?  


this is for my girlfriends spare pc, she likes little kids games.

---

### Post by jan quark on 2008-01-04
try to launch it via the terminal
and report the error messages which are showing up

---

### Post by jan quark on 2008-01-04
...

I have just installed the game via Synaptic

the python dependencies were also installed

then I started the game via the terminal (bouncy)

and this came out```
michal@ubuntu:~$ bouncy
***** glibc detected *** python: free(): invalid pointer: 0x0906c588 *****
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7de6d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7dea800]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb783ad81]
/usr/lib/libapt-pkg-libc6.6-6.so.4.5(_Z13ReadConfigDirR13ConfigurationRKSsbj+0x317)[0xabb26487]
/usr/lib/libapt-pkg-libc6.6-6.so.4.5(_Z13pkgInitConfigR13Configuration+0x82b)[0xabb5baab]
                           .
                           .
                           .
I cut out the long part
                           .
                           .
                           .
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
**Aborted (core dumped)**

```

can't run the game either yet

---

### Post by Huzudra on 2008-01-05
hmm glad to know its not just me having the problem.  thanks for the help, i appreciate it!

---

### Post by LancerNZ on 2008-04-20
I'm also having black window issues with this one, downloaded via Synaptic.

---

### Post by dru08 on 2008-05-03
Hi am having black screen when running bouncy.... complete newbie running Mint Linux which is a Ubuntu distro.... i ran it from the terminal as suggested in this thread and below is the returned messages...

Traceback (most recent call last):
  File "game.py", line 188, in <module>
    game.menu()
  File "game.py", line 104, in menu
    anchor=(pyglyph.Align.center, pyglyph.Align.top))
  File "/usr/share/games/bouncy/pyglyph/layout.py", line 347, in draw
    glColor(style.color)
  File "/usr/lib/python2.5/site-packages/OpenGL/GL/exceptional.py", line 207, in glColor
    function = glColorDispatch[arrays.GLfloatArray.arraySize( arg )]
KeyError: 1


any help in interpreting this would be much appreciated.

Thanks to all

---

