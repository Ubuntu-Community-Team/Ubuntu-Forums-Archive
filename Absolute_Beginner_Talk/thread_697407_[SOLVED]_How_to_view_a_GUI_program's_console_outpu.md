---
title: "[SOLVED] How to view a GUI program's console output?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by dOgS0c on 2008-02-15
Is there a way to view what a GUI program writes to the console, other than launching it from a terminal window? Sometimes when I launch a program and it crashes, I'd like to see any messages it might have issued. In FreeBSD I would just press Ctrl+Alt+F1 and see the program's console output, but in Ubuntu I have to open a terminal and launch the program again.

By the way, in FreeBSD I could press Ctrl+Alt+F1 then press ScrollLock and use arrow keys to scroll. Can I enable this feature in Ubuntu?

---

### Post by hyper_ch on 2008-02-15
most programs do have a log file which you can check or then syslog.

---

### Post by dOgS0c on 2008-02-15
Many (most?) GUI programs don't have a log, and many don't write anything to syslog either. But most of them write something to stdout. Do you always have to run them twice to see what it is?

---

### Post by trippinnik on 2008-02-15
you could also run the program in the console.

---

### Post by Joeb454 on 2008-02-15
I think what the OP means is that if a program crashes, he can't press Ctrl+Alt+F1 like in FreeBSD to see the output it **would** give, if run from a terminal.

And I can't think of anything off the top of my head other than running it again :(

---

### Post by dOgS0c on 2008-02-15
> **trippinnik said:**
> you could also run the program in the console.

Yes, that's what I have to do. But when the program crashes, I have to open a console and launch it AGAIN, which is inconvenient. How can I see what the program has ALREADY printed?

---

### Post by LuisC-SM on 2008-02-15
> **dOgS0c said:**
> Yes, that's what I have to do. But when the program crashes, I have to open a console and launch it AGAIN, which is inconvenient. How can I see what the program has ALREADY printed?

Wrong...
First open a console (terminal)
Then run the command...
If something happens you will be able to see the output of what caused the crashed.... this is the information you must post to let people help you.

Cheers.

Luis.

PS. I think that you are right clicking (doble clciking) and executing the comands on a terminal.... if so... do it as I said then post your prlblem

EDIT: If you are using Nautilus or konqueror and you are using your mouse to double click  (similar o M$ windows) most probabily for some programs that have spaces in the middle ....eg: Age of Empires... the correct way to run it ion a terminal is something like this:$  /path/to/your/file/Age\ of\ Empires

---

### Post by dOgS0c on 2008-02-15
> **LuisC-SM said:**
> First open a console (terminal)

What if I open Nautilus first and run the executable from there? Where has all the text gone that I would have seen in a terminal? :) Like I said, in the FreeBSD distribution I use I can see it by simply pressing Ctrl-Alt-F1. It's more convenient than opening a console and runnning the program again.

---

### Post by justleen on 2008-02-15
/dev/null


unless the programm specificly "made" to log the output some where, you wont find the output..

obvious place to start looking is /var/log, wether something is logged or not, but most applications wont log there normally..

you could change/create  the shortcuts , adding "myexe.sh 2&>1 /path/to/application.log"  to it... might work..

---

### Post by dOgS0c on 2008-02-15
Okay, I found it. If a program doesn't have a terminal, its output goes to ~/.xsession-errors. Simple as that. :)

---

