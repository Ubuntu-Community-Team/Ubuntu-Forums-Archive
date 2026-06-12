---
title: "libc6 error when installing canon driver"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by donthavacluebuntu on 2007-08-19
Hello.

I was trying to install a canon driver for edgy 6.10 and received the error:  " error: dependency is not satisfiable: libc6"

I have the current version of libc6 from the repos.  The driver may be designed for feisty only.  Is it possible that it would only work on that version or should it be compatible with both versions?  Would that cause this error?

Thanks

---

### Post by afzalnaj on 2007-08-19
yes probably...it might need a higher version...try unpacking the package using a third party util...local the control.tar.gz open it

then open the control file to see exactly which version it wants

---

### Post by donthavacluebuntu on 2007-08-19
Which thrid party utility do you suggest?

---

