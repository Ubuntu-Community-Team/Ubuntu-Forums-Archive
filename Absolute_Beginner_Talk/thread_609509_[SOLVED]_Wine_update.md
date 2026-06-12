---
title: "[SOLVED] Wine update"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-11-11
Two updates were just installed by the update manager today.

I only use one application with Wine - Mailwasher and I find that the program will now no longer launch.  A message appears saying Starting Mailwasher and that then closes but the program does not launch.

Do I need to change something in Wine or is this just a bug which might go away with the next Wine update?

---

### Post by atomkarinca on 2007-11-11
you can try launching the program from the terminal and see if there are any errors show up. if not, it's probably a bug.

---

### Post by expatCM on 2007-11-11
Good suggestion.  I think it may be a permissions problem ....

I entered the command and got a response ".wine is not owned by you"    So then I put sudo at the beginning of the line and Mailwasher started.

I start Mailwasher from System / Preferences / Sessions.  I think that if I add sudo to the start of the command there it will not work without the password which is not what I want.  

So is there a way of adding the password here or should I be trying some other approach to change the permissions of the program / Wine?

---

### Post by expatCM on 2007-11-11
on reflection, perhaps the best way to approach this is with the .wine directory which appears to be root / root at present...

---

