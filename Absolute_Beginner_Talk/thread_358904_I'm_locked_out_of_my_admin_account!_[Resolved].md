---
title: "I'm locked out of my admin account! [Resolved]"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Jimpdx on 2007-02-11
I'm less than 48 hours into my Ubuntu 6.06 experience and I'm already facing a crisis.  Suddenly, I can't log in to my original account, the only one that has administrative privileges.  I get a DOS-like black screen with indecipherable symbols at the top, then I get redirected to the logon screen.  The second account doesn't seem to have any access to troubleshooting features.  Any suggestions?

---

### Post by scrooge_74 on 2007-02-11
reboot and use recovery mode and then if you get to a command prompt type startx
go into the user management and change the password to your first user

---

### Post by Jimpdx on 2007-02-11
Thank you for the reply.  I tried what you suggested and it took me to the non-admin account, so I could not modify any user parameters.  I'm beginning to suspect that my original account doesn't exist anymore!  Any suggestions on how to proceed would be appreciated.

---

### Post by nickoli_02 on 2007-02-12
Just to clear things up... the "non-admin" account would be the account you log in and use as a normal user. "admin" is the root user. When you boot into recovery mode I believe you're automatically logged in as root, so you will definitely be able to change anything you want.

I highly doubt your user account was accidentally deleted. Did you install/change anything before this situation occurred? Some config files probably got a little messed up

---

### Post by aysiu on 2007-02-12
This should help:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by Jimpdx on 2007-02-12
Thank you both for replying.  I came up with a workaround that involved using Terminal (in recovery mode) to access users-admin, allowing my remaining account to perform administrative tasks, creating a new account and deleting the defective account.  So far, so good!

---

### Post by aysiu on 2007-02-12
I'm glad it worked out. For future reference, you don't have to delete the "defective" account. You can just make sure it belongs to the *admin* group. In recovery mode: ```
adduser defectiveone admin
reboot
```

---

