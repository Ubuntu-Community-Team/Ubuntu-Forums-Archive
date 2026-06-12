---
title: "Can ubuntu extract rar files or what programme do i need?"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Drazy on 2006-10-05
^^

---

### Post by Ben Sprinkle on 2006-10-05
[http://rarlabs.com](http://rarlabs.com)
Get the linux version extract then go in your terminal and type this:
```

cd Desktop/rarfolder
./unrar e rarfile.rar

```
And that should work mate.

---

### Post by divague on 2006-10-05
sudo apt-get install rar

this is gonna install a program that let you handle .rar files

---

### Post by jaboua on 2006-10-05
```
sudo aptitude install unrar
```

EDIT: Seems like I was a bit late :P

---

### Post by Drazy on 2006-10-05
thanks

---

### Post by saxophobe on 2006-10-06
I got this to work by using the following cmd:

```
cd /home/usrname/rardir
rar e rarfile.rar
```

Or, once installed, you can right click and select 'Extract here' from the context menu.

Just another approach.  Hope it helps someone!

sax

---

