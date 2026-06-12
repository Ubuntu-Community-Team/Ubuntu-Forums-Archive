---
title: "Problem installing ANY file manager."
date: 2008-06-12
forum: BSD
---

### Post by Barrucadu on 2008-06-12
I've tried a few different file managers and they all fail at this point:

```

/usr/bin/ld: cannot find -lgio-2.0

```

Whilst compiling libgiofam.

---

### Post by ibutho on 2008-06-12
Apparently gio-2.0 is provided by glib 2, so try reinstalling the glib20 package.

---

