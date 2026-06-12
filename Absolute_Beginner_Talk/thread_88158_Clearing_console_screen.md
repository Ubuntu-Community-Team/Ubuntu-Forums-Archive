---
title: "Clearing console screen"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by ramdisc on 2005-11-09
Hello,

How do I clear the console screen so it would look like as if I just opened it?  I don't like long contents.

Thanks in advance.

---

### Post by gord on 2005-11-09
```

clear

```
just type that in ;)

---

### Post by Kvark on 2005-11-09
You can also decrease the amount of lines that are saved so you can scroll up in gnome's terminal window at Current Profile in the Edit menu. Under the tab Scrolling.

---

### Post by 23meg on 2005-11-09
Ctrl + L also works.

---

### Post by ssam on 2005-11-09
also if some command has messed up the teminal try the
```
reset
```
command.

this is often needed it you try to display a binary file, try
```
cat /dev/urandom
```
then ctrl+c to stop it.
some times in amoun the 8 bit data is a terminal control sequence that changes the display mode of the terminal. it can cause all the letters to be replaced by symbols, strange colours (eg, black on black), and other stuff. a quick reset usually fixes it.

---

