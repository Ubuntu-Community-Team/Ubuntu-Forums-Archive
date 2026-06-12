---
title: "[SOLVED] pidgin not responding"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by AnLGP on 2008-03-25
Every time I log into pidgin it says "Buddy List not responding" then it basically tells me I need to "force quit" to shut it down or I can "wait".  I've tried waiting but the same prompt pops up and I am eventually forced to quit the program.  It was working 3 days ago.

Help!

Thanks!

---

### Post by Hospadar on 2008-03-25
I would try two things:
First, purge and re-install pidgin, you can do this with synaptic, or from a command line:```
sudo apt-get remove --purge pidgin
sudo apt-get install pidgin
```

If that doesn't work, purge the installation again (the first command), then delete the ".purple" directory that contains your pidgin config, either on the command line ```
 rm -rf ~/.purple
``` or Ctrl-H in a file browser to see hidden files, go to your home directory, delete the .purple folder.  Now re-install pidgin (the second command from option one).

---

### Post by AnLGP on 2008-03-25
The second one worked, removing the ~/.purple then reinstalling

---

### Post by jellylogix on 2008-05-21
the second method also worked for me... thank you

---

### Post by simon_ives on 2008-07-24
Thanks, purge and reinstall got it going for me too.

---

### Post by brokencode on 2008-07-24
same problem here. found this thread over google and I should join this awesome forum. Thanks for your help ;)

---

