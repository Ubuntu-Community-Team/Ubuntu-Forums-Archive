---
title: "[SOLVED] Missing C header files?"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by t0p on 2008-01-01
I'm learning to program in C.  But I haven't done any in a while, since installing Gutsy.

Last night, I copied over a source file.  It began with:

```
#include <stdio.h>
#include <stdlib.h>
```

When I ran **gcc**, it told me

```
heap.c:1:19: error: stdio.h: No such file or directory
heap.c:2:20: error: stdlib.h: No such file or directory

```

Now, I never had this kind of problem when I was using Feisty.  Am I right in thinking that the C header files aren't included in a default Gutsy installation?  And what package/s do I need to install to enable me to compile C source code okay?

---

### Post by taurus on 2008-01-01
You need the build-essential package.  Have you installed it yet?

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by t0p on 2008-01-01
> **taurus said:**
> You need the build-essential package.  Have you installed it yet?


Aha!! No, I haven't installed build-essential.  But I shall now.  Thanks, taurus!

---

