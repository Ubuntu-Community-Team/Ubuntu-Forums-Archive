---
title: "syntax help please"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by lionround on 2007-10-09
I am sure this is SOOO basic, but here goes.

I have a directory /home/david/.wine/drive_c/Program Files.  If I try to get to it in Terminal it tells me "No such directory".  However, if I browse to it, it is there.  So, I renamed it without the space, ProgramFiles and can get to it Terminal.

Question:  How do you get to a directory with a space in the name in Terminal?

Thanks,

---

### Post by bodhi.zazen on 2007-10-09
The command line does not like the space in "program file"

so :

cd /home/david/.wine/drive_c/Program\ Files
cd "/home/david/.wine/drive_c/Program Files"

Or use tab completion 

cd ~/.wi<tab>/drive_c/Pro<tab>

Tab completion works for commands too.

---

### Post by lionround on 2007-10-09
cd /home/david/.wine/drive_c/Program\ Files

Thanks, worked like a charm.

---

### Post by bodhi.zazen on 2007-10-09
Try tab completion, you will love it ...

---

### Post by CaptainInsaneO on 2007-10-09
Tab completion has saved my butt numerous times in all things Linux and Cisco. :lolflag:

---

