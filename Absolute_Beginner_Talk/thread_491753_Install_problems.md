---
title: "Install problems"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Istonian on 2007-07-04
Whenever I try to install something using the terminal I get this message...E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.. 

I have tried correcting it how it said, but it said I needed superuser privilges.

---

### Post by haricharan on 2007-07-04
use
```
 sudo dpkg --configure -a
``` to gain access to superuser privileges.....

---

### Post by Vajra Vrtti on 2007-07-04
The command is:
> **sudo dpkg --configure -a**
It will ask your password to execute.

---

### Post by Istonian on 2007-07-04
wow, i knew that, I don't know why I didn't think of that. Thank you for you're brilliance.

---

### Post by mrdav1e on 2007-07-11
vmware wants a serial number, i just tabbed over to cancel, clicked enter, and the installation proceded.
this was what i encountered with the dpkg error

---

