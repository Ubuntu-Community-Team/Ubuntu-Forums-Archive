---
title: "Can top be used to continuously display dmesg?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by kevdog on 2008-03-04
Can I use the command top or any other command to continuously display the dmesg log?  I'd like to view the log continuously when typing certain commands to immediately spot an error if there is any.

---

### Post by mrsteveman1 on 2008-03-04
You can use tail here, for instance for the /var/log/messages file:
```

tail -f /var/log/messages
```

Most kernel messages get piped through syslog anyway which means most of them end up in the messages file.

---

### Post by Oldsoldier2003 on 2008-03-04
> **mrsteveman1 said:**
> You can use tail here, for instance for the /var/log/messages file:
```

tail -f /var/log/messages
```

Most kernel messages get piped through syslog anyway which means most of them end up in the messages file.

depending on how his logging is set up he may not get the desired result.

```
tail -f /var/log/dmesg
``` worked better on the server I just checked because tailing messages just gave me a bunch of mark lines...

---

### Post by mrsteveman1 on 2008-03-04
Yea some syslog setups don't keep all the kernel messages, and i have noticed ubuntu sticks in a lot of MARK lines for some reason.

I never noticed the dmesg file though :D

---

### Post by p_quarles on 2008-03-04
This would be a good job for conky. The line would look something like this:
```
execi 20 dmesg | tail
```
Use the "-n" option with tail to control how many lines it displays in conky.

---

### Post by Oldsoldier2003 on 2008-03-04
> **p_quarles said:**
> This would be a good job for conky. The line would look something like this:
```
execi 20 dmesg | tail
```
Use the "-n" option with tail to control how many lines it displays in conky.
Hmm I might have to try conky, I've heard about it a couple times the past couple days so it might be worth checking out....

---

