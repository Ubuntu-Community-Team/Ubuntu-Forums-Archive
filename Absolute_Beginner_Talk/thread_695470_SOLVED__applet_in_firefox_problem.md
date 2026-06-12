---
title: "SOLVED:  applet in firefox problem"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by richieboy on 2008-02-13
this worked for me.

in your home directory find .mozilla.  nb: it is a hidden file.  note the dot.  in .mozilla you'll see the firefox directory.  in that one you'll see another directory, mine begins n3rrq.  look for a file named XUL.mfasl.  i don't know what this is or what it does.  DO THIS AT YOUR OWN RISK.  it worked for me.  make XUL.mfasl executable.  in the terminal i typed:

chmod 777 XUL.mfasl

and now my applets load and work.  if any admins see this post please let me know if i've done something wrong or harmful.

i hope this helps some of you.

rich

---

