---
title: "When grep, how do I remove duplicates?"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2006-11-18
```

$ grep wh file
what
what
what
when
where
who
why

```

What do I need to pipe in order to have it only display 1 of the duplicates?

The result should look like this:

```

$ grep wh file
what
when
where
who
why

```

---

### Post by lloyd_b on 2006-11-19
```
**grep wh file | sort -u**
```

Will produce a sorted list, and suppress any duplicates.  Offhand, I don't know of a way to get rid of the duplicates without sorting.....

Lloyd B.

---

