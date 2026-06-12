---
title: "install glib"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by yahn on 2007-07-03
I'm trying to install glib so that I can use Anjuta because every time I try to build something I get the error make *** no targets specified and no makefile found.  But when I try to install glib I get the exact same error.  I've installed everything else in the list Anjuta gives before trying to compile something, so I'm kind of confused why I'm getting this error and how I would fix it.

Can someone please help?

Thank you.

---

### Post by Raineer on 2007-07-03
Are you doing:
```
sudo apt-get install build-essentials libglib2.0-0 libglib2.0-0-dev
```

This should work.

That being said, "no makefile found" means you aren't running
```
./configure
``` or it is erroring out by missing a dependcy (which....could be glib ;p )

---

### Post by yahn on 2007-07-03
error can't find package libglib2.0-0-dev.
error can't find package build-essentials.

---

### Post by Raineer on 2007-07-03
BAH

it's ```
libglib2.0-dev
```

sorry :(

This is why you need to type as fast as you think, the build-essential is singular and not plural

---

### Post by yahn on 2007-07-03
Thank you very much.

But now I'm getting errors for libgnomeui and gtk+-2.0.  I tried to apt-get install them, but it was saying those packages couldn't be found either.  Would you by chance know how to fix this?

---

### Post by Raineer on 2007-07-03
libgtk2.0-0 and libgtk2.0-dev
libgnomeui-0 and libgnomeui-dev

You can search for these packages at [http://packages.ubuntu.com](http://packages.ubuntu.com)  as well, it's a great resource.

---

