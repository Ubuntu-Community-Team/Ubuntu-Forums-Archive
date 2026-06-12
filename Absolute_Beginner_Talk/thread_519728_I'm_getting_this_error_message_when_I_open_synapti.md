---
title: "I'm getting this error message when I open synaptic."
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by richardwad1 on 2007-08-07
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I was running the update manager and the computer froze while it was configuring a package. I think it was one named vino that it froze on.Any ideas on how to fix this? It won't let me go into synaptic package manager now.

---

### Post by deadgobby on 2007-08-07
That is simple
 Open up the Terminal and type in this command
sudo dpkg --configure -a
 It will ask for a password and should be the one you logged into the splash screen with.
Gobby

---

### Post by richardwad1 on 2007-08-07
Thanks. I already fixed it actually. I used "sudo dselect"

Thanks for your help though!

---

