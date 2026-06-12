---
title: "The panel has encountered a fatal error ..."
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2008-03-27
I get this error:

The panel has encountered a fatal error

The panel could not register with the bonobo-activation server (error code: 3) and will exit. 
It may be automatically restarted.


What in the world is this?  Never heard of bonobo.

Carl

---

### Post by cwmoser on 2008-03-27
I found the solution to this.  This error occurred when I was using NXServer to remote into my home PC.  When I got home and tried to log in, all I got was a black screen - no desktop icons - just the menu bar at the top.  

I tried to run nautilus from the command prompt.

I solved this via:  sudo apt-get install nautilus and presto my desktop and icons came back.

Carl

---

