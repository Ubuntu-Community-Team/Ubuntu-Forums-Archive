---
title: "Autoboot cannot open file?"
date: 2008-07-30
forum: Apple Hardware Users
---

### Post by redbaritone on 2008-07-30
I'm trying to use the autoboot binary, included in ppc-utilities, to enable server mode so that the machine automatically boots after a power outage. (This is for Dapper 6.0.6 LTS server, on a dual-core G5.) 

command:
sudo autoboot on

leads to the error:
open: No such file or directory

Exactly what file is it trying to open? Any help would be greatly appreciated.

---

### Post by tiresia on 2008-07-31
The file you are missing is /sbin/autoboot
If you don't have it, you must install the powerpc-utils suite.

```
sudo apt-get install powerpc-utils
```

---

### Post by redbaritone on 2008-07-31
Thanks, but I've installed ppc-utilities.

$ which autoboot
/sbin/autoboot

---

### Post by tiresia on 2008-07-31
That's strange…It looks like you have the command in your path, but it is not really installed?!
I guess, that you get the same result if you do

```
sudo /sbin/autoboot on
```

---

