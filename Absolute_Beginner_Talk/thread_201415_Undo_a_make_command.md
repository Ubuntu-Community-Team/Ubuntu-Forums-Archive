---
title: "Undo a make command?"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by yteh on 2006-06-21
Pardon my in-experience. Is there a way I can undo a make command? Please advise. Thanks.

---

### Post by localzuk on 2006-06-21
Just delete all the compiled files. However, it depends if it was a plain 'make' or something like a 'make install'. If it was the prior, you should have a bunch of binary files (or just one) which you can just delete (or you could try 'make clean'. If the latter, take a look in the makefile for an option such as 'uninstall' or 'remove'. If there is one, then run 'make uninstall' (replacing uninstall with whatever command it was). Else you would have to track down the files and remove them by hand I'm afraid.

---

### Post by PhilOSparta on 2006-06-21
I guess you need to explain more of what you want.
When you use the make command, you usually create an executable program.
Possibly the make will over-write the original program.  It that's the case, you can't undo it.  i.e. the original was over written and replaced by the new command.  You would have to reload the original program.

---

### Post by yteh on 2006-06-21
Thanks for the quick responses. It was a 'make' rather than a 'make install'. Went with localzuk's suggestion. Things are back to normal.

---

