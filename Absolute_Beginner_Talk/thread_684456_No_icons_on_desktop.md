---
title: "No icons on desktop"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by munch3 on 2008-02-01
Can I remove the ahrd drive icons from my desktop without unmounting them?
I rly like it when there r no icons on the desktop :)

---

### Post by renzokuken on 2008-02-01
open a terminal and run ```
gconf-editor
```

go to

apps > nautilus > desktop

and **uncheck** the **volumes visible** box

close and exit and they should be gone, may have to log out and back in again.

---

### Post by munch3 on 2008-02-01
It worked tyvm!

---

