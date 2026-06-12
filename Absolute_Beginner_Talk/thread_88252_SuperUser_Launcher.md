---
title: "SuperUser Launcher"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by quintok on 2005-11-09
Hi,
I've just installed Textpad (win32 editor) using wine and was wondering how I made wine load it as a superuser through a launcher?  I can do it through a terminal but it seems rather verbose:

quintok@pc1:~$ su
Password:
root@pc1:/home/quintok# wine "/home/quintok/.wine/drive_c/Program Files/TextPad 4/TextPad.exe"

Ideally I'd like it to popup with a password request like synaptic does but if I have to hard code it into the launcher that's fine.
Thanks

---

### Post by gord on 2005-11-09
this should work for you :)
```
gksudo wine "/home/quintok/.wine/drive_c/Program Files/TextPad 4/TextPad.exe"
```

---

### Post by quintok on 2005-11-09
I didn't realise it was going to pass paramaters like it did, so here's how I finally got it to work:
```
gksudo "wine /home/quintok/.wine/drive_c/Program\ Files/TextPad\ 4/TextPad.exe"
```

thanks alot!

---

