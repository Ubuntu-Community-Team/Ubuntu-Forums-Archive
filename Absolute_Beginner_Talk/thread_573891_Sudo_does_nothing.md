---
title: "Sudo does nothing"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by Rephab on 2007-10-12
I've a problem with "sudo" command.
The first time i use it in a terminal, it asks me for a password... i put the password without problems, then he does nothing with every command i use.

sudo gedit /....  does nothing, also sudo chmod ... etc etc.

if i put only "sudo" i can see the options.
If i use gedit or chmod whitout sudo i cannot edit files as user without permissions (work as intended ^^)

Anyone knows where is the problem?

Thank you.

---

### Post by lisati on 2007-10-12
For sudo to do its work, you need to be logged on with an account with "administrator" privileges.

---

### Post by banewman on 2007-10-12
I'm using feisty and have the same problem every now and again. The easiest solution I've found is to reboot - then sudo works ok. If you have the problem all the time then a check in users and groups to see if the user is allowed to administer the system would be a good start. :)

---

### Post by Indefual on 2007-10-12
> **lisati said:**
> For sudo to do its work, you need to be logged on with an account with "administrator" privileges.

My assumption is that the user is logged in as the default user that Ubuntu creates when it sets up.  In that account (assuming the original poster didn't create another account) it should work, right?

No mention of an error is listed.  That would list an error I think.

But, anyway, it works for me after the password prompt.  Rephab: Does it give an error message?

Banewman: That's really weird.  That shouldn't effect it, I don't think.

---

### Post by Rephab on 2007-10-12
Solved it thank you!

The user i logged wasn't in admin group.

:)

---

### Post by banewman on 2007-10-12
The sudo problem only occurred after I removed some packages...

---

