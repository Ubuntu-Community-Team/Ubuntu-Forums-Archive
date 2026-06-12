---
title: "[SOLVED] can't access Synaptic"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Abacab on 2008-02-25
hi.

everything was working fine and then today when I booted up the pc and tried to access synaptic I got the following message:

E: Malformed line 47 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

It will only let me click on close. Can anyone tell me how to get back synaptic access please?

---

### Post by Abacab on 2008-02-25
argh now I feel really foolish. I've been struggling with this for 3 hours then when I finally post for help I fix it within minutes. Sorry. As you were. Couldn't see an option to delete the post so I'll just mark it solved.

---

### Post by thisiam on 2008-02-25
how do did you solve it?

---

### Post by Abacab on 2008-02-25
I went to /etc/apt/sources.list & clicked on the file. Whereas I couldn't access it in synaptic it now opened for me and I tried unticking the 3rd party software lists. I then restarted synaptic and re-enabled the boxes I'd unticked and it's now back to normal. It was just a guess and trial and error but it worked.

---

