---
title: "Down loaded wine Now what?"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Afrikprophet on 2008-01-19
Hi I just dl ed wine thru the add/remove applications menu but it does not show up on my applications list. I don't really know what to do now? do I just pop in a pc program and see what happens or what?

---

### Post by peabody on 2008-01-19
You should now be able to attempt to open Windows x86 programs by double-clicking on them in Nautilus.  With wine, there are never any guarantees.  For additional information, you can try searching the applications database at [http://appdb.winehq.org/](http://appdb.winehq.org/).

---

### Post by JoshuaRL on 2008-01-19
That's weird, it should register in the Applications menu.  It should be at the bottom in a sub-menu of it's own.  But I suggest using the newest one from their website, since it's always in development.

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Also, run this after to make sure you have it configured right:

```

wineconfig

```

---

### Post by asmoore82 on 2008-01-19
> **JoshuaRL said:**
> That's weird, it should register in the Applications menu.  It should be at the bottom in a sub-menu of it's own.  But I suggest using the newest one from their website, since it's always in development.

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Also, run this after to make sure you have it configured right:

```

wineconfig

```

it's actually ```
winecfg
```

but first and foremost you must understand that WINE is primarily a **command line** tool.
Most win32 programs don't have a chance at running correctly unless you
hold their hand on what PATH environment they need.

from the command line is also the only way you can get feedback from WINE
on what is and what is not working properly.

---

