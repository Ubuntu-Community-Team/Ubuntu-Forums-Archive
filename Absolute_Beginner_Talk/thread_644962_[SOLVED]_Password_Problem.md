---
title: "[SOLVED] Password Problem? ? ?"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by bobd104 on 2007-12-19
Believe it or not, I just installed Ubuntu and during the install process assigned a user ID and Password.  Problem is, when I try to logon it says the user id or password is incorrect?  The only thing I can think of is that I typed my user ID or password incorrectly by mistake and now I cannot get it to recognize and so I'm locked out?  Is there anything I can do?

---

### Post by aysiu on 2007-12-19
Yes, you can reset the password:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Cypher on 2007-12-19
Yes..in the GRUB menu you get when you start the PC, choose the Recovery option (usually the 2nd one) and this will boot the machine but drop you to a shell with ROOT access. Here you can reset the password for your user account with:
```

passwd <username>

```
Now reboot the machine and boot up normally and use your new password to get in.

---

### Post by bobd104 on 2007-12-19
Thank you all.  The problem is now fixed. . .

---

