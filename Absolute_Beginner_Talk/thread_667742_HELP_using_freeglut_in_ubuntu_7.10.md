---
title: "HELP using freeglut in ubuntu 7.10"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by bat3man on 2008-01-14
I'm trying to compile some code that makes use of GLUT, but ubuntu doesn't seem to like it, and won't recognise the inclusion of glut.h:

error: GL/glut.h: No such file or directory

I've checked to see that freeglut is updated.  What could I be doing wrong?

---

### Post by melopsittacus on 2008-01-14
Where is your glut.h located? I am using it as well, and it is in  /usr/include/GL/ and the compiler has no problems finding it.

Perhaps try both
```
#include "GL/glut.h"
```

and

```
#include <GL/glut.h>
```

and see if either of them works.

---

