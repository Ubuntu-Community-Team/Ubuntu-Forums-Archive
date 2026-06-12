---
title: "Removing # from filenames"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by taddy_porter on 2007-08-22
I have a directory with movie files filled with the # sign. Kaffeine can't open them in Konqueror. Is there an easy way to remove them via the shell?

---

### Post by moephan on 2007-08-22
Not sure if I'm missing something, but couldn't you just do

```

mv #filename.wmv filename.wmv

```

---

### Post by taddy_porter on 2007-08-22
There are about 150 files.

---

### Post by croto on 2007-08-22
How about something like
```

rename 's/#//g' *

```

That should remove all # signs. I'd suggest replacing the # symbols by underscores:

```

rename 's/#/_/g' *

```

---

### Post by taddy_porter on 2007-08-23
Perfect. Thanks.

---

