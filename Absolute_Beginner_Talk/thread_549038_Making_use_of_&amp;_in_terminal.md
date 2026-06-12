---
title: "Making use of &amp; in terminal"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by silverace99 on 2007-09-12
noob here.

Back when I was in school, I used a little linux for the technical software we ran for classes. Normally closing a terminal that you start a program with will terminate that program, so I took to appending "&" to my commands. As a result I could close the terminal and the program would continue to function. I believe I was using Redhat.

I can't seem to be able to do the same thing in Ubuntu. Closing the terminal even after running the program independtly of it (i.e. "gaim &") still stopped the program from working.

So my question is, what is the Ubuntu equivalent to "&"?

---

### Post by eentonig on 2007-09-12
running it from <ALT>+<F2> is the first that comes to mind

---

### Post by silverace99 on 2007-09-12
ok, good idea. But lets say for some reason I absolutely want to run it from a terminal. How would I achieve the same thing in Ubuntu as when I type "gaim &" in redhat?

---

### Post by paradoc on 2007-09-12
Was it not a &&, not an &?

---

### Post by kellemes on 2007-09-12
This probably has to do with how Bash is setup.. maybe you should dive into that.

---

### Post by hyper_ch on 2007-09-12
Hmmm, to make it all simple you could use "screen" :)

In "screen" you can open multiple virtual terminals and run stuff in there... then you can detach the screen and the stuff keeps on running...
The great thing is then, that you can resume the screen session from another location... this means you will get the same virtual terminals at work at the same stage where you left them in the morning at home...

---

### Post by mali2297 on 2007-09-12
Before you close the terminal, type *disown*. Then you will not kill the background process.

---

### Post by asmoore82 on 2007-09-12
> **mali2297 said:**
> Before you close the terminal, type *disown*. Then you will not kill the background process.

while **disown** -ing before closing the terminal is good practice,
it is generally not neccessary;

I just tested out 'gaim &' and closing the terminal on my Ubuntu 7.04 system
and gaim didn't die.
are you *sure* gaim is not still running (it will minimize itself to the "notification area")?
if you don't have the "notification area" in your setup, check for gaim like this
```
~$ ps -A | grep aim
```

(( you can also background a process in BASH (terminal shell) *after* it is already open.
to do this, hit Ctrl+Z in the terminal to temporarily stop the program,
then type '**bg**' and enter to cause the program to continue operation in the background,
this is equivalent to originally running it with the '&'))

---

### Post by mali2297 on 2007-09-12
For additional tips, see here:
[http://ubuntuforums.org/showthread.php?t=528138](http://ubuntuforums.org/showthread.php?t=528138)

---

