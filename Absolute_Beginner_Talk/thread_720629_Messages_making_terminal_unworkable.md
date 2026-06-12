---
title: "Messages making terminal unworkable"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by familyman on 2008-03-10
When I work in the regular terminal I get the following:
[  861.091590] sd 2:0:0:2: [sdd] Sense Key : Illegal Request [current] 
[  861.091598] sd 2:0:0:2: [sdd] Add. Sense: Logical unit not supported
[  861.092713] sd 2:0:0:2: [sdd] Test WP failed, assume Write Enabled
[  861.092718] sd 2:0:0:2: [sdd] Assuming drive cache: write through

And then 1000x times. Making it very difficult to follow what I am doing. It is also filling my dmesg so that it becomes unusable unless I run it a lot of times after another in the hope that I catch the message I am looking for.

Can anybody please suggest a method for this message not being logged, nor in my terminal, nor in dmesg? It is really upsetting my debugging efforts. These are necessary enough with the whole SLUB/SLAB and ATI configuration thing.

---

### Post by handydan918 on 2008-03-11
no clue about the messages, but can you switch tty's?
Ya know, just ctrl+alt+F3 or some such?

---

### Post by familyman on 2008-03-11
Yes I can, but these messages appear in every terminal. Only when I start the terminal from X they do not appear.

The speed at which these messages appear mean that I cannot even type a single command without being interrupted. The commands parse properly though.

---

### Post by handydan918 on 2008-03-12
I dunno, man.  I've never seen this one before...
What have you tried? Does it happen in recovery mode? And why are you working in console? That is SO  1985....:)

How are you getting to a console loggin in the first place? Does the same thing happen with a terminal wndow (emulator)?

---

