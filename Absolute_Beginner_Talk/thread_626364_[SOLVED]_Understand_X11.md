---
title: "[SOLVED] Understand X11"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by dwhitney67 on 2007-11-29
I'm not new to Unix nor Linux, however after all the years I've been working with such, I've never fully understood the intricacies/details of X11.

Is there a way to instruct/configure X11 to disregard the input when a user enters ctrl-alt-bksp or ctrl-alt-Fn?

---

### Post by FuturePilot on 2007-11-29
Yes you can disable the Ctrl+Alt+Backspace by adding 
```
Option "DontZap" "yes"
```
to the Server section in your xorg.conf
I'm not sure about the other one though.

---

### Post by dwhitney67 on 2007-11-29
Good enough for me.  Thanks for the reply and the valuable information.

I believe one way to prevent the user from summoning up a console is to edit the /etc/inittab file... but perhaps there is a better way?

---

### Post by dwhitney67 on 2007-11-29
> **FuturePilot said:**
> Yes you can disable the Ctrl+Alt+Backspace by adding 
```
Option "DontZap" "yes"
```
to the Server section in your xorg.conf
I'm not sure about the other one though.

Btw, where does this option go??  In other words, what section? 


Ahhh.... stupid question, please disregard.  I re-read your earlier response again and the answer is there.

---

