---
title: "how do i write a cron"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by bigb0i on 2007-12-18
how do i write a cron entry to display "happy independence day" at noon on july 4th each year?

how do i write a cron entry to display "happy new year"at midnight of the jan 1 each y ear in the motd?

thanks,

---

### Post by thelatinist on 2007-12-18
What do you want to display these things in?  cron will execute a command, but you need to know what the command will be...

The cron tab will look like this:

```

0 12 4 7 * *command to be executed on July 4*
0 0 1 1 * *command to be executed on January 1*
```

I suppose you could write a "Hello, world!" script.

---

### Post by macogw on 2007-12-18
Check this site out. [http://www.scrounge.org/linux/cron.html](http://www.scrounge.org/linux/cron.html)

---

### Post by Dr Small on 2007-12-18
```
@yearly figlet -ct "Happy New Year" > /etc/motd
```

---

### Post by macogw on 2007-12-18
> **Dr Small said:**
> ```
@yearly figlet -ct "Happy New Year" > /etc/motd
```
ooo that's like the pop up big text thing in the address book on osx and like quicksilver does.  thank you!  also, yay so that's where the login text comes from!  i learned something.

don't know what the @yearly is though.  i'm guessing that's motd syntax that will work for new years?  for fourth of july, still have to use cron, but hey, now we know that the command to use is figlet

---

### Post by thelatinist on 2007-12-18
> **macogw said:**
> but hey, now we know that the command to use is figlet

So...

```
0 12 4 7 * figlet -ct "Happy Independence Day" > /etc/motd
```

?

---

### Post by macogw on 2007-12-19
> **thelatinist said:**
> So...

```
0 12 4 7 * figlet -ct "Happy Independence Day" > /etc/motd
```

?

I think you'd want to have something else that runs the next day to remove it back from there.  That'll only do it if you login from the terminal though.

Hmm apparently figlet isn't like the nice "show big text" thing on the osx addressbook and quicksilver.  I wanna find one that does it in the GUI, because that's only in the command line.

---

