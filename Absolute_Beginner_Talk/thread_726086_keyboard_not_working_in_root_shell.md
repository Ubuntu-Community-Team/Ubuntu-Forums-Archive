---
title: "keyboard not working in root shell"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by tanmoy.talukdar on 2008-03-16
It's sometimes now i have been using Ubuntu. and i 've run into quite an interesting problem.

i m using Ubuntu 7.10 on my Intel-based PC with Microsoft-provided keyboard.
I was playing with it a bit. I added "rw init=/bin/bash" after the "kernel....." line in grub and it gave me a root shell.

but then the impossible occurred.My keyboard stopped responding :confused: 

to b specific sometimes while i type commands i cant see them but if i press return they 'r executed and sometimes they show some meaningless behavior !!!

but when i boot it up normally ;the keyboard works fine...(as i m typing this message :) )

so friends , please look into the matter and let me know if there is any workaround or i m doing some mistake or really its an OS bug...........

---

### Post by cmnorton on 2008-03-16
If you have access to a regular keyboard, does this problem occur then? I know very little about X configuration, but this almost sounds like an X permissions/configuration problem, and beyond telling you to experiment with configuring X -- preserve your original X configuration first -- I am at a loss.

---

### Post by tanmoy.talukdar on 2008-03-16
i m doin this with my regular keyboard,which,otherwise works fine

and another thing 
while doing init=/bin/bash how does the X thing comes into play ???

---

### Post by cmnorton on 2008-03-17
I must have misunderstood your original post. It mentions a Microsoft keyboard.

As to X,, I though X-terms were still governed by X as opposed to logging in without a GUI. A

---

