---
title: "c compiler"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by meistwer on 2006-03-18
Hi there,

I'm trying to complie a *.c file in ubuntu but I don't seem to know how to:confused: . I use 

    cc filename -o filename.c

It's not working and I'd like to se the output in the command window.

Any help please?

Thanks a lot

---

### Post by Ubuntuud on 2006-03-18
try gcc instead of cc

---

### Post by meistwer on 2006-03-18
Hi,

I've tried 

gcc filename -o filename.c

and 

g++ filename -o filename.c

didnt work either, :(

---

### Post by taurus on 2006-03-18
Install build-essential and all would be good again...
```

sudo apt-get install build-essential

```

---

### Post by David Marrs on 2006-03-18
[QUOTE=meistwer]Hi there,

I'm trying to complie a *.c file in ubuntu but I don't seem to know how to:confused: . I use 

    cc filename -o filename.c
[/QUOTE]
You've got the syntax wrong. The output file (set with -o) is filename so you should write:
cc filename.c -o filename

Then run with ./filename

---

