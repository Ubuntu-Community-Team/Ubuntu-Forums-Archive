---
title: "Left panel in nautilus"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by ronb94 on 2008-02-23
Hello
Suddenly the left panel in nautilus gone.How can I restore it?
Thanks

---

### Post by y-lee on 2008-02-23
**View-->Side Panel **in Nautilus's menu or hit **F9**

---

### Post by ronb94 on 2008-02-23
Its already marked.

---

### Post by y-lee on 2008-02-23
Hmm

try shutting down Nautilus and then

```
gconf-editor
```

go to **apps -->nautilus-->preferences**

now make sure **start_with_sidebar** clicked and also check **sidebar_width** to make sure it is not 0

---

### Post by seventhc on 2008-02-23
Maybe you slid it over, so it would still be open but collapsed.
See if when you put your cursor at the left edge if you can drag it open.
The cursor would change to a double arrow.

---

### Post by ronb94 on 2008-02-23
> **y-lee said:**
> Hmm

try shutting down Nautilus and then

```
gconf-editor
```

go to **apps -->nautilus-->preferences**

now make sure **start_with_sidebar** clicked and also check **sidebar_width** to make sure it is not 0

Thanks its worked

---

