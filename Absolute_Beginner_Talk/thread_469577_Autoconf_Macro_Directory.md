---
title: "Autoconf Macro Directory"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by matteospqr on 2007-06-10
Hello!

Does anyone know where the autoconf macro directory is?

thanks

---

### Post by reclusivemonkey on 2007-06-10
> **matteospqr said:**
> Hello!

Does anyone know where the autoconf macro directory is?

thanks

I'm not sure what you mean by that. Can you expand a little?

---

### Post by reader4 on 2007-06-11
I'm not sure, but a search of:

```
find / -name *.m4
```

yields the following directories with results on my system:

```

/usr/share/aclocal/
/usr/share/doc/m4/examples/
/usr/share/autoconf/autoconf/
/usr/share/autoconf/m4sugar/
/usr/share/autoconf/autotest/
/usr/share/aclocal-1.9/
/usr/share/libtool/

```

I'd go with ```
/usr/share/autoconf/autoconf/
```

---

