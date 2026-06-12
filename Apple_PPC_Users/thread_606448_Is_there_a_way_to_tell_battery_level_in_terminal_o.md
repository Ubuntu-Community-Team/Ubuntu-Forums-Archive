---
title: "Is there a way to tell battery level in terminal on PPC?"
date: 2007-11-07
forum: Apple PPC Users
---

### Post by ticopelp on 2007-11-07
[sudo] acpi -b doesn't work on my Powerbook, which is the solution I found via search. Is there a different command to tell the battery time remaining on PowerPC machines? 

Thanks.

---

### Post by maop on 2007-11-08
In ubuntu ppc this works:

```

$ cat /proc/apm

```

:wink:

---

### Post by ticopelp on 2007-11-09
Thanks very much!

---

