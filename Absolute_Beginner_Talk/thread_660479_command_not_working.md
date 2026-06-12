---
title: "command not working"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Thumper! on 2008-01-06
hi there

i'm trying to get the following comment to work but it saying that permission is denied

command -
```
ndiswrapper -i NetA5AGU.inf
```

answer -
```
couldn't create /etc/ndiswrapper/neta5agu: Permission denied at /usr/sbin/ndiswrapper-1.9 line 152.
```

this is in terminal

Thanks for your help!

Tom

---

### Post by Blutack on 2008-01-06
You need to use sudo to give yourself the required permissions.

sudo ndiswrapper -i NetA5AGU.inf 
should do the trick

---

### Post by Thumper! on 2008-01-06
```
couldn't open NetA5AGU.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
```

That what i get now...thanks very much though...have any ideas now?

---

### Post by jfinkels on 2008-01-06
> **Thumper! said:**
> ```
couldn't open NetA5AGU.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
```

That what i get now...thanks very much though...have any ideas now?

Are you in the directory containing the file "NetA5AGU.inf" ?

---

### Post by Thumper! on 2008-01-06
yep sorted now, thanks.....!

---

