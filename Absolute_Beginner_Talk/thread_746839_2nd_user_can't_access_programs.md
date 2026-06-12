---
title: "2nd user can't access programs"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by wooly on 2008-04-05
I used System>Administration>Users and Groups to add a second user account on my computer. 

I can open a shell as me, cd to /home/newuser, and create a file with:
    ** john@thinkpad:/home/newuser$ gedit testfile**
... and the file exists.

But when I **"su newuser"**
and execute **"gedit testfile"**, I get:
[B]Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.
[/B]

What can I do to give this user access to programs?

---

### Post by zvacet on 2008-04-06
Did you tried to login as** newuser** and then see if **newuser** have access to the programs?

---

