---
title: "Default Accounts"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Stringsy on 2007-08-22
I looked in the /etc/passwd file and noticed there was a **** load of default accounts....

mail, news, games, daemon, nobody

Should I disable them all for security?

---

### Post by toidi on 2007-08-22
Just checked mine and it is the same so I would say a big no.  It appears these accounts are for parts of the OS.

---

### Post by Stringsy on 2007-08-22
Well I know it's part of the OS... but surely these are just more potential security risks if they never actually get used?

---

### Post by schorsch on 2007-08-22
Almost all of them do not have a password if you check the second field in /etc/shadow after the username:
```
sudo cat /etc/shadow
```
but they are required to run several daemons.

---

### Post by djroze on 2007-08-22
I think these accounts exist so that various processes can have appropriate permissions set for resources.  For example, a CD burning program could have write access to a CD drive (or something like that).  So, you might have problems with various programs not being able to access files if you delete those accounts - I wouldn't recommend deleting them.

---

### Post by schorsch on 2007-08-22
Yeah, as they do not have any password there (and so cannot login!) they are no security risc. Just leave them as they are, you could run into big trouble if you delete them.

---

