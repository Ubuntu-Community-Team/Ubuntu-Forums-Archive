---
title: "Fake NES can't install"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by grogger13 on 2007-03-21
```
mike@mike-laptop:~/fakenes-0.5.8$ make
cc -O2 -W -Wall -o cbuild cbuild.c
./cbuild
Creating directory build/unix/...
you're missing one or more of: AllegroGL, OpenGL, GLU
continuing on without them...
you're missing HawkNL
continuing on without it...
you're missing one or more of: OpenAL, ALUT
continuing on without them...
you're missing zlib
continuing on without it...
you're missing Allegro, silly
please install at least version 4.2 or higher
bailing out...
make: *** [exec] Error 1
mike@mike-laptop:~/fakenes-0.5.8$ make
./cbuild
you're missing one or more of: AllegroGL, OpenGL, GLU
continuing on without them...
you're missing HawkNL
continuing on without it...
you're missing one or more of: OpenAL, ALUT
continuing on without them...
you're missing zlib
continuing on without it...
you're missing Allegro, silly
please install at least version 4.2 or higher
bailing out...
make: *** [exec] Error 1

```

The first command is before i installed the liballegro4.2 file and the second is after, dont quite know what im doing wrong.

---

### Post by salsafyren on 2007-03-30
You need the -dev package of allegro.

I just compiled fakenes now.

---

