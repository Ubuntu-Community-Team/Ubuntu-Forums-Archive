---
title: "How do I give a user config access to a particular interface?"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by jimmwill on 2006-03-05
I would like to give a user the right to modify a particular interface without giving them general root access.  They will need to use an application that requires them to use libnet.so.0.  Right now I can't get this to work without giving the users root access.  I don't mind them having access to a particular interface becuast I will only give them access to a virtual interface that will be dot1q tagged out the main interface.  Any ideas on the right way to do this?

---

### Post by aysiu on 2006-03-05
What do you mean by "interface"? Are you a programmer?

If it's a *file* you want to give them access to, just change the permissions on that file using the *chmod* command.

---

