---
title: "amsn reset help"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by halesquad on 2007-06-13
I am using amsn and i am getting no joy with the auto sign in or the webcam.

All i want to do is sign in without any hassle, i keep on getting the message in the attached message.

i have tryed to delete all the other accounts but it  doesn't let me 

any ideas 

Thanks 

Stephen

---

### Post by shearn89 on 2007-06-13
try killing all instances of amsn, then signing on. In terminal:

```
kill $(pgrep amsn)
```

then restart amsn.

---

### Post by halesquad on 2007-06-13
stephen@stephen-desktop:~$ kill $(pgrep amsn)
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
stephen@stephen-desktop:~$ kill $(pgrep amsn)
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
stephen@stephen-desktop:~$ 


this is the outcome i did it twice 

is that correct ??

---

### Post by shearn89 on 2007-06-13
> **halesquad said:**
> stephen@stephen-desktop:~$ kill $(pgrep amsn)
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
stephen@stephen-desktop:~$ kill $(pgrep amsn)
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
stephen@stephen-desktop:~$ 


this is the outcome i did it twice 

is that correct ??


yes - that just means that the "pgrep" command (which finds the id number of the process stated after it) couldn't find amsn, so its not running....

---

### Post by halesquad on 2007-06-13
so now what do i do

---

### Post by shearn89 on 2007-06-13
not entirely sure... I'm not that hot on amsn, as i use gaim. Sorry...

---

### Post by halesquad on 2007-06-13
can you get webcam on gaim

---

### Post by shearn89 on 2007-06-13
I'm not sure. I think the new version (renamed Pidgin) does - you'll have to google it.

---

