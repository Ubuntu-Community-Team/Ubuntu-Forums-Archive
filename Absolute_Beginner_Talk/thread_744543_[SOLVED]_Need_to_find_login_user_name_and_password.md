---
title: "[SOLVED] Need to find login user name and password on Linux computer"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by CyberDean on 2008-04-03
I am working on a Ubuntu 7.10 computer I picked up this morning but I do not know the login user name or password.  During the last two months of searching the forums I did run across a thread with instructions on how to retreive the user name and password, but now I can't find that thread.  Can't do anything till I login, any help?  :confused:

---

### Post by Iowan on 2008-04-03
Check [here]("http://www.psychocats.net/ubuntu/resetpassword").

---

### Post by horan116 on 2008-04-03
You cannot view your password in Linux because Linux used shadow passwords.

```
cd etc/
vim passwd
```

In here your first user you created starts with the user id at 1000 but it should look like 
$user: x:1000:1000

The x stands for shadow passwords. 

You can have proof of this by showing the encrypted password by viewing the shadow file

So sorry but your better off having to reinstall

---

