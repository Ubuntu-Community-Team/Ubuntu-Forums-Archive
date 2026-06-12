---
title: "patching /usr/include/GL/glxproto.h"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by DannyX0 on 2006-02-12
I've been trying to get this to work all day long:
[http://www.ubuntuforums.org/showthread.php?t=127090&highlight=xgl](http://www.ubuntuforums.org/showthread.php?t=127090&highlight=xgl)
OK, so far so good, util I came to this
> 
We have to patch /usr/include/GL/glxproto.h also:
```
cd /usr/include/GL/
sudo cp glxproto.h glxproto.bak
sudo patch -p0 <~/Mesa/glxproto.patch
```

But when I do the cd I get : No such file or directory
so, I chose to cd to where I put Mesa, and cd into the /include/GL/ folder
I run the first sudo and it asks for pass, which is nothing then it says:
```
cp: cannot stat `glxproto.h': No such file or directory
``` !!!
Somebody Please Help Me!
I like linux so far... I'm glad I changed from Win. but this is making me think twice, since I'm new at all this stuff.  :cry:

---

### Post by DannyX0 on 2006-02-12
Come on! Could someone please tell me how they did it? At least?

---

### Post by soulglo83 on 2006-02-14
same problem /usr/include/GL does not contain glxproto.h, i tried downloading file from a google search but patching it failed. how can we populate this directory? what program or settings are we lacking?

---

