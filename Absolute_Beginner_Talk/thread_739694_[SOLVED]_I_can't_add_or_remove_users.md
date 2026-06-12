---
title: "[SOLVED] I can't add or remove users"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by JohnLynch on 2008-03-30
I accidentally removed myself as admin, with no other admin accounts in my install. I have set a password and can login as sudo (or su) through a terminal, but I don't know how to add an admin through this way or set myself as admin once again as an alternative.

---

### Post by rkd on 2008-03-30
I think that if you enter the command 

gdm

in the terminal, it will start up X, then you can login and have the GUI to use to correct the user account settings.

No doubt there is a way to do it from the command line, but I don't know it and would have to look it up.  This seems like a quicker way to get you going.

---

### Post by JohnLynch on 2008-03-30
I'm a bit confused what you mean by that. I opened up the terminal and gdm won't launch. So I reset the computer and log into root at the recover mode. Then I launch gdm and it launches the login screen like normal. I try to login as root and it fails so I try to login as my user and I still can't get to the users and groups option in System.

So what did I do wrong?

---

### Post by rkd on 2008-03-30
You probably didn't do anything wrong.  Now that you describe what happened, I seem to remember that Ubuntu has a specific check not to accept root at the GUI login.  That restriction can be removed, but the only way I know of to remove it is in the GUI. Catch 22.

I'll ponder and/or research some and try to come back fairly quickly with another suggestion.

---

### Post by rkd on 2008-03-30
It appears to be pretty simple to fix.

Login as root and enter the command```
gpasswd -a username admin
```where username is the login name that you want to become an administrator.  

I guess you would do this after booting into recover mode.  Then boot normally and your user should be an administrator again.

---

### Post by JohnLynch on 2008-03-30
This worked perfectly, thankyou :)

---

