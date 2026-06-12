---
title: "easy ubuntu"
date: 2006-08-23
forum: Apple PPC Users
---

### Post by urmom9388 on 2006-08-23
i cannot use easy ubuntu on my ibook g4. When i try to execute the program I get this output:
```
erik@erik-laptop:~/easyubuntu$ sudo python easyubuntu.in
System sanity check: Failed!
Errors:
--------
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

EasyUbuntu is now trying to run 'dpkg --configure -a'
System sanity check: Failed!
Errors:
--------
dpkg: status database area is locked by another process

EasyUbuntu will not run before these errors are fixed. Please fix them and try again
erik@erik-laptop:~/easyubuntu$

```
Is there aything I can do to fix this?

---

### Post by avtolle on 2006-08-23
Looks like you have Update Manager running, or possibly Synaptic; close the one that is running, and try again.

---

### Post by spinz8 on 2006-08-23
Hi, 
I have installed the appropriate codecs and other stuffs via easyubuntu but easyubutnu is not found on the menu lists?. Any idea where i can locate it to relaunch it in future?
Thanks

---

### Post by urmom9388 on 2006-08-23
search easy ubuntu in google and find the answer

now that synaptic is closed it launches but when I try to install the programs I get an error that says: Could not apply changes! Fix broken packages first.

---

