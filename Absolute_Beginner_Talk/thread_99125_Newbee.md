---
title: "Newbee"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by jcsaturn on 2005-12-05
Hello all who are experienced and new.


I just insatlled the software. I forgot my user name and password after the install. Any suggestions?

---

### Post by Qrk on 2005-12-05
reinstall. 

You can't do anything without a username and password; and if you could, the devolpers would try to fix it.

---

### Post by amohanty on 2005-12-05
Have you tried dropping into the recovery console, ie selecting the entry called ... [recovery mode]... in the screen which prompts you what to boot.

If you can, then try the following command:

```
cat /etc/passwd
```

That should get you a list of the users registered with the system. See if you recognize yours.

AM

---

### Post by funkydan2 on 2005-12-05
cat /etc/passwd will only get you your username - but that might be enough to jog your memory.

If you've only just installed ubuntu, then I'd just run through the installer again and this time *write down your username/password*

---

### Post by amohanty on 2005-12-05
```
cat /etc/passwd will only get you your username - but that might be enough to jog your memory.
```

The intention was that once he/she gets their username to be able to just do a 

```
passwd <username>
```

I am not sure about whether the recovery console drops you in with root auth but I think I read elsewhere on the forums that it does. Please correct me if I am wrong on this.

Thanks.
AM

---

