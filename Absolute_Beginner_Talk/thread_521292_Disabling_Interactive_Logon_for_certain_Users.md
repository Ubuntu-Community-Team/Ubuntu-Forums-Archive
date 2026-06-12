---
title: "Disabling Interactive Logon for certain Users"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Poorly Sketched Idiot on 2007-08-09
Hi There.

Is there a way to disable a user's ability to log in interactively?

I created a user specifically to be used only with Samba shares and I don't want my entire house to be able to log into my machine through X.

I am using Kubuntu Feisty.

Cheers.

---

### Post by schorsch on 2007-08-09
Add the following line to the file /etc/shells

```
/bin/false
```

and change the shell for the mentioned user to /bin/false in the file /etc/passwd. It is the last entry in the line with the username in front.

---

