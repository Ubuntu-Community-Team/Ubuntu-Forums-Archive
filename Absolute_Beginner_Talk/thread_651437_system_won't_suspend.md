---
title: "system won't suspend"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by ADH on 2007-12-27
Using 7.10, I get an error message when the system tried to suspend.  Help said to check the FAQ, but I couldn't find them.

Firestarter also didn't start during bootup.

Thanks,

---

### Post by syczu on 2007-12-27
The most common reason for this notification is that the current user does not have permission to suspend or hibernate the computer.

You should use it in terminal 

Example:
   apmsleep +1:15    will suspend for one hour and 15 minutes
   apmsleep 8:00     will suspend until 8:00 am

And do it with sudo

Example:
   sudo apmsleep +1:15

Hope this will help.

---

