---
title: "Java on MacBook Pro running 7.10"
date: 2008-01-17
forum: Apple Intel Users
---

### Post by tmas on 2008-01-17
I cant get the JRE to work on 7.10!
Have tried JRE5,6 and 7 without any success..

Anyone got a hint on what to do?

---

### Post by cvasilak on 2008-01-18
Probably is not your fault.

The latest security updates unfortunately broke Java and wxWidgets applications. See [https://launchpad.net/bugs/183969](https://launchpad.net/bugs/183969) for more information. The X.org package causing the problem has been pulled from the repositories, which is why you currently get a "403 Forbidden" error.


Wait a bit for the fix

Regards,
Christos

---

