---
title: "[SOLVED] Compiz and Emerald Theme Manger Problems"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Promaster91 on 2008-02-29
Hi, I just recently installed Emerald Theme Manger with compiz. I am having some problems with it. This is the code i was told to start the theme.
```

compiz --replace -c emerald

```

But this comes up...

```

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (core) - Warn: Unknown option '-c'

```

/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'emerald'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


It applies the theme sometimes but none of the window toolbar (minimize, maximize, close) come up. It sometimes does, however, I am not able to move the window. Can somebody help me? Thanks[HTML][/HTML]

---

### Post by olskar on 2008-02-29
compiz --replace && emerald --replace

try that :)

---

### Post by Promaster91 on 2008-02-29
No luck... does the same thing.

---

### Post by glennric on 2008-02-29
Try doing those as separate commands.
```
compiz --replace &
emerald --replace &
```

---

### Post by glennric on 2008-02-29
The first command you tried won't work at all. 
compiz --replace -c emerald
is passing a parameter "-c" to compiz, which it doesn't know about, and then telling compiz to load the plugin "emerald", but emerald is not a plugin for compiz.

---

### Post by major_rocks on 2008-02-29
```
emerald --replace
```

should work

---

### Post by Promaster91 on 2008-03-28
Hey it worked thanks.

---

### Post by CrazyAzn on 2008-05-09
> **major_rocks said:**
> ```
emerald --replace
```

should work

it worked for me but then as soon as i closed terminal it stopped working and the borders disappeared =/

---

### Post by major_rocks on 2008-05-09
try this, go to........

main menu > system > preferences > sessions - click the "add" button, then in the "name" field enter Emerald, in the "command" field enter emerald --replace, click ok, then close.

ctrl + alt + backspace to restart x, and you should be good to go.

---

