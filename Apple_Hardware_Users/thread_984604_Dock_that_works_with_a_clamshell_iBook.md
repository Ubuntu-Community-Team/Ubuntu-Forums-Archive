---
title: "Dock that works with a clamshell iBook?"
date: 2008-11-16
forum: Apple Hardware Users
---

### Post by stir-crazy on 2008-11-16
Simply put, trying to find a dock that works with a clamshell iBook.  Tried installing AWN, but that is demanding compiz-fusion. 
```
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

```
Tried running compiz, get this:
```
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 
```

Not sure what to do.  Simdock seems to work well, EXCEPT that it permanently occupies the screen to the extent I have the zoom set...so no go.

I can't find kiba-dock in the repositories, but then it seems I'm having major issues with the repositories on my PPC's the past couple of weeks :confused:

So, if somebody can tell me if I can get AWN running on this old a machine, cool!  I really like it on my i386, but that has substantially better specs.  That or any other dock that will simply launch apps, but that will hide behind applications when needed.

Thanks!

---

### Post by Peter76 on 2008-11-29
Try runnin metacity with as a compositor; in gconf-editor under apps -> metacity mark the compositing option. You need Intrepid though; apparantly Hardy's version was a bit buggy

---

