---
title: "in which package is 'dict'"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2007-11-06
I asked this before in the programming section, but i think this is more of a geenral question so it would fit better in here.

After i updated to fiesty i haven't ben able to use a very handy application called **tksqlite**
i need the **tcl dict module**.

Here's the trace so you can see exactly what i am missing.

```
$ ./tksqlite.tcl
Error in startup script: can't find package dict
    while executing
"package require dict"
    invoked from within
"if {[info tclversion] < 8.5} {
package require dict
}"
    (file "./tksqlite.tcl" line 123)
```

---

