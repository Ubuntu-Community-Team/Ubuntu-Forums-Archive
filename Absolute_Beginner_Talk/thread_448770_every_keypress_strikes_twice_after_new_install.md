---
title: "every keypress strikes twice after new install"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-05-19
On a new install of ubuntustudio I end up in a terminal rather than in the     gnome desktop,  and have great difficulty doing anything because every keypress produces two characters, making     it impossible to type any sensible command. Even DEL deletes two at a time. 

I can see two entries in the log, maybe relevant? I don't know:

failed    to set xfermod (error mask =0x40)
ATA abnormal status 0x7F on port 0x0001F807


Nothing else looks as though it's reporting an error

---

### Post by VoidBoy on 2007-05-23
My guess is that your keyboard is not configured well.

go to system-preferences-keyboard................
then, where it says "Delay", make sure the button is located somewhere between the 
beginning and the middle of the bar.
Example:
    \-------------===--------/-----------------------------

---

### Post by ginestre on 2007-05-23
Thanks, but I can't: I'm in a terminal and I can't type any single letters!- so I can't get out.

---

