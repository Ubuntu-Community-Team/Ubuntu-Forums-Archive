---
title: "deb file not open???"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by erez1012 on 2005-10-23
i download aprogram and i click the file.deb and it dont opend
thanks
i book 3g

---

### Post by PriceChild on 2005-10-23
I'm trying to work out the same thing, as well as how to navigate using the terminal... i take it that "cd" doesn't work in linux? should really try it now before asking!

---

### Post by jeremy on 2005-10-23
To install from a .deb you should do:
sudo dpkg -i xxx.deb 
where xxx= the name of the .deb file

---

### Post by Snakey on 2005-10-23
cd does work, try dir first to see what the correct directoryname is,  a space, should be placed after a backslash (or put the whole directory between quotes)

```
cd ~/my\ directory
cd '~/my directory'
```

---

### Post by Kyral on 2005-10-23
*points to the link below for Terminal "Orientation"*

---

