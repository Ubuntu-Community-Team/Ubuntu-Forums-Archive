---
title: "How do I uninstall Frostwire?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by moebob24 on 2008-01-09
How do I get this done when Frostwire is not shown in the ADD/REMOVE menu?

Also Frostwire would never run either. Any time I clicked it nothing would happen.

---

### Post by santiagoward2000 on 2008-01-09
> **moebob24 said:**
> How do I get this done when Frostwire is not shown in the ADD/REMOVE menu?
Hi!
Just go to System/Synaptic package manager, look for it there and remove it.

> **moebob24 said:**
> Also Frostwire would never run either. Any time I clicked it nothing would happen.

About this, have you installed java? Try opening a terminal, type:
```
frostwire
```
and see what errors you get.
Cheers!

---

### Post by moebob24 on 2008-01-09
```
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
ls: /usr/lib/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com

```

hahahah yeah that would explain it not working. 

Thanks for the help tho:)

---

### Post by santiagoward2000 on 2008-01-09
> **moebob24 said:**
> ```
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
ls: /usr/lib/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com

```

hahahah yeah that would explain it not working. 

Thanks for the help tho:)

You're welcome!
Just to be sure, you can use Add/Remove to install Java6. It's easier than installing the one from [www.java.com](www.java.com) and it works fine.
Cheers!

---

