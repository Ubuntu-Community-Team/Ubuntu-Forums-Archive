---
title: "is there a way to terminate programs after a delay in the terminal?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by ssaamon on 2007-10-24
I was wondering how I would write a bash script to run a program and then terminate it after a delay?

say to open firefox for instance, then 20 seconds later close it.

thanks,
saamon

---

### Post by Billy_McBong on 2007-10-24
[COLOR="Blue"]you can use sleep to make it wait, for example "sleep 20" would make it wait 20 seconds

and i know there is some command that terminates programs but i don't know what it is. i wanna say its "kill" but im not sure[/COLOR]

---

### Post by -grubby on 2007-10-24
> **Billy_McBong said:**
> [COLOR="Blue"]you can use sleep to make it wait, for example "sleep 20" would make it wait 20 seconds

and i know there is some command that terminates programs but i don't know what it is. i wanna say its "kill" but im not sure[/COLOR]

xkill

---

### Post by rorestuff on 2007-10-24
You can try:

sleep 20 && killall firefox-bin

---

