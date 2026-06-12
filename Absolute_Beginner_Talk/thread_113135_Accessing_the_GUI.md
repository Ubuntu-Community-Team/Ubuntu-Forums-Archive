---
title: "Accessing the GUI"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by drothe on 2006-01-05
So, I just installed Ubuntu on my laptop.  Hit a few packet snags in the install, due to CD issues, so I figured I'd just overlook them until I get my internet installed... but I can't even figure out how to boot the GUI!  I'm at the command line and looking around in the /bin directory hoping for a program to start the GUI, but I'm not seeing one.  vmlinuz looked like the best candidate, but both my user and root don't have permission to use it.  Ideas?  The documentation doesn't say anything about a question -this- low level.  :-(

---

### Post by rjwood on 2006-01-05
go back to your home directory by pressing "cd".

Have you tried to reboot?

type "startx"--see if that works--

---

### Post by Zelut on 2006-01-05
Well you can try *startx* for starters.  I would also try below for making sure you're up to date (if anything was missed in installation)

*sudo apt-get update && apt-get upgrade*

---

### Post by drothe on 2006-01-05
"startx" and "below" commands not found.  Yeah, I tried restarting.

Looks like we know which packets got messed up... time to try installing again.  Thanks for trying, folks.  :-)

---

### Post by drothe on 2006-01-05
Oh, I can't read.  I saw "below" and thouht you meant a command.  I'm doing the sudo stuff now.  Thanks.  :-)

---

### Post by 23meg on 2006-01-05
Try typing "startx" and if you get any errors, report them.

(edit: oops, too slow)

---

### Post by drothe on 2006-01-05
The sudo command you showed me did fix up some Perl packets, but startx still doesn't exist.

---

