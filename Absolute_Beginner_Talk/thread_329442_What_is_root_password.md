---
title: "What is root password?"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by bazsl on 2007-01-01
I just installed the Ubuntu 6.10 server. The installer did not prompt me for a password for root and I could not find any installation documentation for the server build. What is the default root password or where can I find it?  Thanks.

---

### Post by Tenicus on 2007-01-01
There is no default password.
to set one type: 
sudo passwd root

and then enter the new password twice.

---

### Post by taurus on 2007-01-01
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by stucky on 2007-01-04
Something that would be nice for install developers to include would be some sort of verbage during the user setup section of the install that points out that you are not creating a root account. Also include ubuntu specific sudo instructions during the setup instead of pointing users (here meaning, migrants from other NIXs) to man sudo which most of the above mentioned kind of ignore because they believe they know all there is to know about "their" sudo. It apparently has confused more than one convertee.

---

