---
title: "finch doesnt work (from pidgin)"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by finer recliner on 2007-05-13
i compiled and installed pidgin on my own, and it runs fine, however finch doesnt seem to work:

```

$ finch
-bash: finch: command not found
$ Finch
-bash: Finch: command not found

```


i dont remember seeing any errors while i compiled it. am i missing something or should i reinstall it?

---

### Post by Jeff24K on 2007-05-14
The executable name is, 'finch'.

When you ./configure you should see this at the top of the "status" output...

```
pidgin 2.0.0

Build GTK+ 2.x UI............. : yes
Build console UI.............. : yes
```

If it's "console UI ... no", then most likely some dependency is missing. A wild guess would be the libncurses developer package (libncurses5-dev for Edgy and Feisty), but it could quite possibly be something else. In the top level directory you unpacked the tarball to you should find  a config.log file.

Somewhere in config.log will be the answer if the obvious doesn't pan out. Try grepping it for 'finch'. You might get lucky. ;)

---

### Post by kroiz on 2007-05-14
I dont have finch or pidgin 2 but I usually do
```

sudo updatedb
locate finch

```
when i dont find something.

also try 
```
man -k finch
```

---

### Post by finer recliner on 2007-05-14
@jeff24K: thank you, your idea was correct, i was missing the dev package. thanks :)

---

### Post by ryry0666 on 2007-08-11
Worked perfectly for me. Thanks

---

