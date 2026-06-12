---
title: "Changing root password"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by hfranco on 2006-04-15
How would I go about changing the root password in the terminal?  I haven't lost it I just want to be able to change it.

Thanks

---

### Post by trent dillman on 2006-04-15
log in as root and use passwd

---

### Post by 5-HT on 2006-04-15
From a root login shell: ```
 passwd 
``` 
As a regular user: ```
 sudo passwd root  
```

---

### Post by dermotti on 2006-04-15
You can't login as root unless you enable the root account

---

### Post by trent dillman on 2006-04-15
Technically, you can:

* Recovery mode
* sudo -s -H

---

### Post by hfranco on 2006-04-15
You guys are awesome. Thanks

---

### Post by trent dillman on 2006-04-15
No problem.

---

