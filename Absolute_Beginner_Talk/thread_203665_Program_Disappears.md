---
title: "Program Disappears"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by EWek1 on 2006-06-25
I added a program to the Accessories menu (tn5250).  Whenever I try to run this program from the menu, the menu screen disappears, and the program never appears.  If I check the run in terminal box, the terminal screen appears for a half-second and then disappears completely.  This program does behave properly if called directly from a terminal window, though.
How do I get this program to run in a GUI mode?

---

### Post by Stolie on 2006-06-25
It seems as though TN5250 is a Telnet client. Therefore you actually have to use the command (assuming it's this) 

- tn5250 <ip address>.

Telnet is a tricky beast.

---

### Post by EWek1 on 2006-06-25
Ok, didn't think to include the ip in the command line, but when I did, it did work.
Thanks very much!

---

