---
title: "easy way to install different version of gnumeric?"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by MacD on 2007-03-05
OK- having the problem with gnumeric.  I have tried for hours to install the latest version from source- getting hung up on dependencies.

Is there an easy way (i.e. through synaptic) to get the older stable version?

from the gnumeric forums:

not sure where to "ask the ubuntu guys"?

 Comment #1 from Jean Bréfort  (developer, points: 13)
2006-11-18 08:54 UTC [reply]

Ubuntu 6.10 ships with an unstable development version of gnumeric. 

I can save plot images to png or jpeg with HEAD with not even a warning. I
don't know about copying to OOo, since I don't use it.

Please ask ubuntu guys to revert to stable goffice-0.2.2 and gnumeric-1.6.3


Comment #2 from Emmanuel Pacaud (developer, points: 16)
2006-11-18 16:33 UTC [reply]

Or at least update to last development release.

This issue was fixed some weeks ago.

---

### Post by troymcdavis on 2007-04-02
Try a
```
$ sudo aptitude upgrade
```
and see if that fixes the issue. If it's a known bug and it's been fixed, you might just need to download the update.

---

