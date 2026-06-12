---
title: "[SOLVED] help with a script`"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Riffer on 2007-12-13
I've installed RealPlayer using the ".bin" file from their website.  Of course it screwed up because I'm still a n00b.  I want to uninstall it but they give you a script to run "uninst.sh".  When I try and run it in the terminal I get a message saying that bash doesn't reconize the command.

Any ideas?

---

### Post by HermanAB on 2007-12-13
First you have to make it executable:
$ sudo chmod 755 filename

then run it specifying the present directory:
$ sudo ./filename

In Linux, the present working directory is not in the search path, therefore the "./" which means "here".  Many moons ago, there was a security exploit, for which a simple fix was the removal of the pwd from the search path.  Since nobody can remember what the heck it was all about, it remained.

Cheers,

Herman

---

