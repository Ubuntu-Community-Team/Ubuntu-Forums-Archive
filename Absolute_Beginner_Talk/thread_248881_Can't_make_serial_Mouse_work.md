---
title: "Can't make serial Mouse work"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Tiao on 2006-09-01
It doesnt recognize automatically serial mouses. How should i proceed to make it work?

I tryed changing on "sudo gedit /etc/X11/xorg.conf":

/dev/input/mice

to

/dev/ttys0

After that i get that xserver error and it goes to text mode.

what should i do?

Thanks :D

---

### Post by Tiao on 2006-09-01
Found the solution :KS If anyone with same problem...

the S needed to be capital letter

its ttyS0 and not ttys0 :-\"

---

