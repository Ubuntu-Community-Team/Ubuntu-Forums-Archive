---
title: "Password"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by ironmike on 2007-05-27
If I am in single user mode tty1 or a recovery mode, what is the default root user password?

---

### Post by taurus on 2007-05-27
If you boot into recovery mode, you are logged in as root so no need to use any password.  Don't you get a prompt?

---

### Post by linfidel on 2007-05-27
> **ironmike said:**
> If I am in single user mode tty1 or a recovery mode, what is the default root user password?I don't think there is one - at least I hope not.  It would make the system pretty insecure to have one that most users don't know about.

The docs imply that there isn't one, too.  I set one up myself in the "user's & groups" control panel under System -> administration.  Just use your sudo authority to change the password.  If you can't get to the GUI, perhaps you can log in with your user name and also do it - I haven't actually tried it (I'm new to Ubuntu).

Maybe someone else can offer more help, if you need it.

---

