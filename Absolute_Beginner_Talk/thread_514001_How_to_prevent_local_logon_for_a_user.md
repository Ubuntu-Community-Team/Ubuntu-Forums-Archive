---
title: "How to prevent local logon for a user??"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Nortonw on 2007-07-31
How can I prevent a user from loging on locally to the machine??

I have an Ubuntu VMWare Server and I want to enable an account for people to use the vmware remotely but not be able to logon to the ubuntu host server.

How can I do this?

I basically dont want them to be able to do anything other than use the vmware remotely.


Thanks

---

### Post by rich.bradshaw on 2007-07-31
Can't you just only give them an account on the virtual?

Why would they have usernames/passwords for the host?

---

### Post by Nortonw on 2007-07-31
They need to have remote access to the vmware server console for adding things like cds etc to the session.

---

### Post by PilotJLR on 2007-07-31
If you modify /etc/passwd, you can change their login shell from bash to /sbin/nologin

---

### Post by Nortonw on 2007-07-31
No joy with that.

Although it does restrict access to a command window it still allows the user to login.

---

### Post by Nortonw on 2007-08-01
Bump

Anymore Ideas??

---

### Post by PilotJLR on 2007-08-01
Try also editing /etc/shadow.
Take the user's entry and add a -1 to just to the left of the right-most colon, like so:

testuser:$1$myl2I.lx$8dAUDw/aJdyyh/9RNvJM10:13726:0:99999:7::**-1**:



This should prevent any logon (at least it does on red hat based systems)... not sure if this will prevent authentication from working on the vmware server console, so better check that out too.  ;-)

---

