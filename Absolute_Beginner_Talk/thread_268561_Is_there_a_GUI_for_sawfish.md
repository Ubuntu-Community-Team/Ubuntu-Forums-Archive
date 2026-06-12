---
title: "Is there a GUI for sawfish ?"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by lavikl on 2006-09-30
downloaded and installed the latest version on Dapper.
is  there a GUI for sawfish or just LISP ?

do i need to exit the default Ubuntu WM first ?
and if i do, how do i do it ?

thanks...

---

### Post by Qrk on 2006-09-30
You can exit the default windows manager by typing 

```
killall metacity
```

and start sawfish by 

```
sawfish
```

Metacity may try to restart, so do try

```
sawfish --replace
```

If you want sawfish to start with Gnome, you should add "sawfish" to startup programs

---

### Post by lavikl on 2006-09-30
i used "killall metacity" and like you said it restarted.
I tried "sawfish --replace" but it doesn't recognize the option "replace".
any other options to kill metacity ?

---

