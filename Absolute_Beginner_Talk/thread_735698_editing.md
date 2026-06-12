---
title: "editing"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by windows hater on 2008-03-25
hello im editing files for conky and i am told to issue this command 

sudo vi /etc/X11/xorg.conf

and when i do i see what i need to change but i cant and is this vi a text editor and if so how do i us the one i already have

many thanks in advance

---

### Post by OmahaVike on 2008-03-25
nano is a much easier interface to use for unix beginners.

try:

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by windows hater on 2008-03-25
well i added what i need to add but when i went to re issue the command it didnt show up

---

### Post by teryowen on 2008-03-25
make sure you save the file.

as for VI if you're just curious

basically you move around with the arrows like normal

use 'x' to remove characters
use 'i' for insert mode
and Esc to quit any mode
use ':' followed by 'q' to quit or 'w' to write

its quite complicated and there are many many features and stuff you can do
such as 'A' is to go to the end of the line and insert, 'o' is new line after 'O' is new line before. But its too many to go over but thats the summary, also you can use '!' its the same as ':' but forced.

---

