---
title: "&quot;releasing&quot; a program on terminal"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-09-09
Im using a GNOME terminal, and when I do a command that open a window like

```
gimp
```

I must close gimp to use again the terminal. Is there any way of opening gimp FROM THE TERMINAL and, at the same time, use the terminal?

---

### Post by aks44 on 2007-09-09
Simply add an ampersand at the end of the command, eg.:

```
gimp &
```

---

### Post by Hossie on 2007-09-09
Of course. Just start it with an ampersand at the end, so the shell will start it as a background task. If you already startet it without an ampersand, hit CTRL+Z, then type "bg %1". Or you could use "screen".

---

### Post by Fixman on 2007-09-09
> **aks44 said:**
> Simply add an ampersand at the end of the command, eg.:

```
gimp &
```

Is there a way to do a "quiet" version of this?

---

### Post by Hossie on 2007-09-09
```
gimp >/dev/null 2>&1 &
```

---

### Post by Fixman on 2007-09-09
> **Hossie said:**
> ```
gimp >/dev/null 2>&1 &
```

```
[5] 8278
[4]   Done                    gimp > /dev/null 2>&1
```

That doesn't work

---

### Post by oldos2er on 2007-09-09
Go to 'File,' 'Open Terminal.'

---

### Post by Harpoon on 2007-09-10
Do you know that after you start a program in a terminal, e.g. gimp, you can then open another terminal and use that for whatever other tasks you have?  That is, unless you have some very strong (and unknown to me) reason to want to use ONLY the terminal used to start gimp.

---

