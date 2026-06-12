---
title: "quake 3 demo installation"
date: 2005-08-01
forum: Absolute Beginner Talk
---

### Post by Tymotey on 2005-08-01
I haev quake 3 demo...it's file name is "linuxq3ademo-1.11-6.x86.gz.sh" what should I do? first steps please tell me.tahnks

---

### Post by Majlo on 2005-08-01
Hi ..

Open terminal and write

*sudo ./linuxq3ademo-1.11-6.x86.gz.sh* 

This install the game

---

### Post by fishfork on 2005-08-28
That won't work for this installer - it seems to be messed up.

Try:

```
sudo ./linuxq3ademo-1.11-6.x86.gz.sh -target /tmp/q3
```

That should launch the installer. Once it's installed somewhere, remove the temporary files:

```
sudo rm -rf /tmp/q3
```

Hope you get it working! I'm not sure why they made it so unnecessarily complicated.

---

### Post by btnheazy03 on 2006-04-23
[QUOTE=fishfork]That won't work for this installer - it seems to be messed up.

Try:

```
sudo ./linuxq3ademo-1.11-6.x86.gz.sh -target /tmp/q3
```

That should launch the installer. Once it's installed somewhere, remove the temporary files:

```
sudo rm -rf /tmp/q3
```

Hope you get it working! I'm not sure why they made it so unnecessarily complicated.[/QUOTE]

Bloody hell. I'd buy you a round of fish & chips if I could, mate :KS

---

### Post by SchitzoJoe on 2008-06-17
this still isn't working for me. and it's making me angry. :(

still getting error messages out the ***. picture attached.

---

