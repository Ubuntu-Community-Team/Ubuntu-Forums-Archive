---
title: "double conky???"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by chris200x9 on 2008-01-29
ok I installed conky and fooled around with my ~/.conkyrc file then I pasted in an example i found now I have two conkys, how do I just make them go away?

---

### Post by emarkd on 2008-01-29
from the terminal:

```
pkill conky
```

---

### Post by chris200x9 on 2008-01-29
> **emarkd said:**
> from the terminal:

```
pkill conky
```


it only got ride of 1

---

### Post by emarkd on 2008-01-29
So do a 

```
ps -e | grep conky
```

to get the PID of the remaining stuck process and get rid of it with a 

```
kill -9 whatever
```

I run two instances of Conky myself and sometimes they just lock up.  No idea why.

---

### Post by spiderbatdad on 2008-01-29
if you have 2 .conkyrc scripts, it will run both. Usually from running conky with the -c option.

---

### Post by Nythain on 2008-01-29
just thought id mention for the users future sanity...
pidof <whateverapp>
will get the pid also, and its a little easier to remember than the above command.

also, thanks for the tip on conky runnin both rc's... will that start two conky's, or just one actually instance running both rc's??? i knew i could just load conky twice, once with one rc and once with another, but the ability to run both rc's via one conky would be pretty slick

---

### Post by emarkd on 2008-01-29
Huh, I've been using Linux for years and I didn't know 'pidof'.  Thanks Nythain, I'll file that one away.  It's quite useful.

---

### Post by Nythain on 2008-01-29
hehe... thats ok, i've been using linux for a couple years now and still havent come up with a witty quote like yours :)

---

### Post by bcrom on 2008-01-29
Try overwriting your .conkyrc with one of the config files here: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

then restart conky or reboot.  

I'm lazy, so I stop conky with 
```
ps -e | grep 'conky'
```
which returns 

xxxx ? conky

```
kill xxxx
``` (replace x with number you get)

and restart with Alt+F2 and type conky

---

