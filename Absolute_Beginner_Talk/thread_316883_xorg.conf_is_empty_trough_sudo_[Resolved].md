---
title: "xorg.conf is empty trough sudo? [Resolved]"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by jcrnan on 2006-12-11
If I try and edit the xorg.conf with $ sudo gedit /etx/X11/xorg.conf the file shows up as empty. However if I find the file trough the gui and open it (without root acsess) then it shows up as normal.

I have no clue what is happening... ](*,)

---

### Post by taurus on 2006-12-11
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by victorbrca on 2006-12-11
Try

```
$ gksudo gedit /etc/X11/xorg.conf
```


Vic.

---

### Post by 23meg on 2006-12-11
That's probably because you're mistyping it; it has to be  /et**c**/X11/xorg.conf .

*(Edit: bronze medal)*

---

### Post by ragnar_123 on 2006-12-11
are you sure you did spell it correct, this sounds wierd to me..

---

### Post by konst88 on 2006-12-11
sudo gedit /etc/X11/xorg.conf
etc not etx

---

### Post by jcrnan on 2006-12-11
I just misspelled it here :p It was the gksudo thing. Thanks :)

---

