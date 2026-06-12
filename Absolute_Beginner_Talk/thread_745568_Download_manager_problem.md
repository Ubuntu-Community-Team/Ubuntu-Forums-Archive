---
title: "Download manager problem"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by ronaldo2004 on 2008-04-04
I have a problem with the download manager.I have been running version 7.10 for several months without any problems.
I have recently stopped receiving updates due to the following message - E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
I have gone into terminal to try to sort out the problem but when I rub the command I get the following message - dpkg: requested operation requires superuser privilege.

Can anyone help me with this as I dont know hot to fix the problem.

Thanks.

Alan

---

### Post by stoneybroke on 2008-04-04
You need to log on as the system operator to perform the superuser tasks. So if you used root when you installed Ubuntu you need to log on as the root user.

---

### Post by ronaldo2004 on 2008-04-04
I logon automatically under my own user name and dont know how to logon as root - can you explain how I do this

---

### Post by Oldsoldier2003 on 2008-04-04
> **stoneybroke said:**
> You need to log on as the system operator to perform the superuser tasks. So if you used root when you installed Ubuntu you need to log on as the root user.

no you do not. in fact logging on as root is discouraged. in this case what he needs to do is run the command ```
sudo dpkg --configure -a
```

---

### Post by Oldsoldier2003 on 2008-04-04
> **ronaldo2004 said:**
> I logon automatically under my own user name and dont know how to logon as root - can you explain how I do this

open a terminal and run the command :

```
sudo dpkg --configure -a
```

enter your password when prompted.

after that you should probably run
```

sudo apt-get install -f 
```
and things should sort themselves out. If you have any more problems please post any additional error messages you receive.

---

### Post by ronaldo2004 on 2008-04-04
Nice one - this sorted the problem out.Thanks for your help.

Alan

---

