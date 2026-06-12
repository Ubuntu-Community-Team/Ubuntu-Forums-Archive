---
title: "startx"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by Hotchilli on 2005-12-29
this the error I receive when I startx

hc:smile: 




Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Please consult the The X.Org Foundation support
         at [http://wiki.X.Org](http://wiki.X.Org)
 for help.

---

### Post by rjwood on 2005-12-29
Where are you? Command line? Have you tried rebooting? If so and you still are at the command line do```
sudo rm /tmp/.X0-lock
``` and start again

---

### Post by bernardfrancois on 2006-01-09
I had a similar problem: when I go to another console (CTRL+ALT+F6 is what I did), and I log in and start x (with the startx command), I got the error mentioned above.

After removing that file I could start X, and the other session still worked.

[edit]
I just noticed I couldn't return to the console where I started x for the second time (with CTRL+ALT+F6). It just gives me a non-grapical environement with some text... Probably the error messages of that instance of X.
[/edit]

---

