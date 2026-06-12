---
title: "my .bash_profile doesn't run"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by BriLarks on 2007-05-15
When I open up a terminal session my .bash_profile isn't executed. 
I have to run it by typing:
. .bash_profile

I had a good look and so far haven't found any way to set terminal up to execute the profile. Most threads I've read suggest that the bash profile should be picked up automatically. 

Thanks for the help.

---

### Post by lloyd_b on 2007-05-15
From what I've seen, ".bash_profile" is only executed once per login.  Opening a terminal window within a session does not execute it again.  So if you're making changes to that file, you may need to log off and then back on before the changes take effect.

If you're looking for something a little more responsive, try making your changes to "~/.bashrc" instead - it *is* executed each time you open a terminal window...

Lloyd B.

---

### Post by BriLarks on 2007-05-16
Thanks mate. I made that change and it worked a treat.  :KS

---

