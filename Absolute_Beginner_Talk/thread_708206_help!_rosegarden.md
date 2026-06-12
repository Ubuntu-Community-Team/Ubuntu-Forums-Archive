---
title: "help! rosegarden"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Mick8882003 on 2008-02-26
no sound, regular sound is working.

---

### Post by Crooksey on 2008-02-26
First of, for the benifit of other users..

```

rosegarden 4.1.6.1-1
    audio and MIDI sequencer, score editor, and general-purpose music
    composition and editing application.
```

Have you install the JACK audio server, because without this running, audio plugins won't work.

---

### Post by Mick8882003 on 2008-02-27
Jack runs, but it errors when rose starts up.

---

### Post by Crooksey on 2008-02-27
Can you post the error jack gives?

---

### Post by Mick8882003 on 2008-02-27
mickpc@mickpc-laptop:~$ jack
This is jack 3.1.1 (C)2004 Arne Zellentin <zarne@users.sf.net>
 *warning* You have no standard location set, putting files into the current
           directory. Please consider setting base_dir in ~/.jack3rc.
 *info* matching dir found: ./jack-02128e01
 *error* cdparanoia failed - could not read CD's TOC.

---

