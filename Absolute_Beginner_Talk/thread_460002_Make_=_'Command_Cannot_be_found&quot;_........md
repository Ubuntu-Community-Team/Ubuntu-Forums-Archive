---
title: "Make = 'Command Cannot be found&quot; ......."
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by johnnyboy on 2007-05-31
Dapper Drake --  Dell inspiron laptop -- kernel 2.6.15 - 28 - 386.  System up to date.

On my last 2 attempts at installing programs this has been the message I recieve.  Both programs have a Makefile, and both of their installation instructions begin (after extraction, of course) with the 'make' command.

When fooling around with Makefile components, i have also recieved a multitude of "command  cannot be found" errors -- all pertaining to common linux commands.  Most other commands not associated with compiling work out fine.

Long story short, I'm wondering if my computer has gone fubar, or if this seems to be a correctable problem.

Thanks in advance

---

### Post by Anicka on 2007-05-31
Have you installed the program make? Try "sudo aptitude install build-essential" in the terminal and try again.

---

### Post by johnnyboy on 2007-05-31
Worked A-Okay, thank you.

---

