---
title: "AWN Can't Run"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Jexel on 2007-10-13
I just upgraded to Gutsy RC and I realised that the AWN icon was still there under accessories (even though it's meant to be uninstalled during the upgrade) but clicking it doesn't do anything. I shrugged and merely decided to reinstall AWN. The installation went fine however when I try running AWN through applications it also fails...when I try to run it in terminal it gives me the message

```
avant-window-navigator: error while loading shared libraries: libwnck-1.so.18: cannot open shared object file: No such file or directory

```

Can somebody help me please? Much thanks.

---

### Post by francisco_athens on 2007-10-13
try 

```
sudo apt-get upgrade -f
```

or 

```
sudo apt-get install -f
```

googled the answer here:
[http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=318&page=1&isLive=true](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=318&page=1&isLive=true)

---

### Post by Jexel on 2007-10-13
i've tried that already but it didn't do anything useful for me

---

### Post by francisco_athens on 2007-10-13
hmm how about:

```
sudo apt-get install libwnck-1
```

???


edit: or rather
```
sudo apt-get install libwnck-common
```

---

### Post by francisco_athens on 2007-10-13
its also looking for a specific and old version of libwnck-1 I think.
you can do this
```
cd /usr/lib/
```
```
sudo ln -s libwnck-1.so.22.2.3 libwnck-1.so.18
```

to make a link to the new version...

---

### Post by Jexel on 2007-10-13
oh my thanks a lot! that worked brilliantly!

---

