---
title: "User Authorizaiions question"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by drmoore1 on 2008-04-06
Is there a way to grant a user access to everything without having to ask for the password everytime and is there a way to turn it off altogether?

---

### Post by Michael.Godawski on 2008-04-06
It is not recommend to disable the password for the administrator. You can easily destroy your system by doing so.

See this link [http://ubuntuforums.org/showthread.php?t=716201&highlight=forum+staff](http://ubuntuforums.org/showthread.php?t=716201&highlight=forum+staff)

---

### Post by Oldsoldier2003 on 2008-04-06
> **drmoore1 said:**
> Is there a way to grant a user access to everything without having to ask for the password everytime and is there a way to turn it off altogether?

There is only one user that has access to everything in the system... that is root. logging on as root for daily operation is extremely hazardous as it bypasses all the protections given by the permissions system. Not only that: a simple rm command can delete your entire installation when run by root...

---

### Post by JoshuaRL on 2008-04-06
There is, but we won't tell you how to do it.  That is extremely dangerous for your security, and [this sticky in the Security Forum](http://ubuntuforums.org/showthread.php?t=716201) explains the new policy.

Sudo and limited user access is the backbone of Linux security, and subverting it is the worst thing you can do for your computer.

Well, other than running Windows.  :p

---

### Post by drmoore1 on 2008-04-06
So you can't tell me how to just always allow a user to change the clock for example? I've gone to the authorizations under administration and played with the settings, this doesn't seem to anything though. Do I have to restart before they take effect or can you answer that?

---

### Post by JoshuaRL on 2008-04-06
> **drmoore1 said:**
> So you can't tell me how to just always allow a user to change the clock for example? I've gone to the authorizations under administration and played with the settings, this doesn't seem to anything though. Do I have to restart before they take effect or can you answer that?

So what have you tried and what errors have you encountered?

---

### Post by drmoore1 on 2008-04-06
I tried changing the authorization to no and yes for active consoles but it didnt do anything and I havent gotten any errors.

---

