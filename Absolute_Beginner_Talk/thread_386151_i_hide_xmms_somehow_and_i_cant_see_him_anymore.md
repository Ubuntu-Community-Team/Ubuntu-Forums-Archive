---
title: "i hide xmms somehow and i cant see him anymore"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by fanny on 2007-03-16
can anyone tell me how i bring him back?
and how in ubuntu i can see which process is running?
thanks!

---

### Post by bodhi.zazen on 2007-03-16
For xmms, in a terminal type : ```
xmms -m
```

to see what is running, in a terminal,

```
ps -aux
```

You can search the output with grep :

```
ps -aux | grep xmms
```

You can also try top. In a terminal :```
top
```

---

### Post by annda on 2007-03-16
there is a GUI system monitor too, if you prefer that: system > administration > system monitor. it has a processes tab.

---

### Post by fanny on 2007-03-16
first thanks . 
can you tell me how to add skins? it comes with .wsz file

---

### Post by annda on 2007-03-16
i believe wsz are winamp skins. beep media player supports those.

---

### Post by johnc4510 on 2007-03-16
You can use wsz skins for xmms.
Extract the file in this file in your home folder: /.xmms/skins
To show the hidden files /. in your home folder Ctrl+h
To extract, right click on file and choose extract here

---

### Post by fanny on 2007-03-16
o.k but how do i add this? i dont see any option when i open xmms and right click.

---

### Post by johnc4510 on 2007-03-16
After extraction to /.xmms/skins  
Right click in the upper left corner of player
A drop down menu should appear
Choose Options>Skin Browser
This will open the skin browser to choose what skin you want

---

### Post by fanny on 2007-03-16
thnks.

---

