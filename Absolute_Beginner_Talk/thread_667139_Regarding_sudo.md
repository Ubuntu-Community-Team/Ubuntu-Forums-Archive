---
title: "Regarding sudo"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by HuBaghdadi on 2008-01-14
Hi.
Whenever I want to perform and administration task, I use sudo su
Suppose I have many accounts on my Ubuntu, does this mean that every user will be able to run:
sudo su 
?
How to disable this command for other users?
Thanks.

---

### Post by njparton on 2008-01-14
Make sure sudo has it's own password that only you know - don't give it to anyone else.

There are probably ways of disabling access to sudo for groups of users, but I would think that's dangerous - mess it up and you could lose access and be looking at a reinstall.

Keep the password secret and hard to guess.

---

### Post by RomeReactor on 2008-01-14
Hi. If your account is the first one on the system, then your password can be used with sudo and gksudo; if you then created more accounts, you can manage their privileges by going to 'System->Administration->Users and Groups'.  There, highlight the accounts you want to restrict, press "Properties", go to the "User Privileges" tab, and make sure **Administer the system** is unchecked. More on using [sudo here]("https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29").

---

### Post by eye208 on 2008-01-14
> **HuBaghdadi said:**
> Whenever I want to perform and administration task, I use sudo su
Suppose I have many accounts on my Ubuntu, does this mean that every user will be able to run:
sudo su 
?
How to disable this command for other users?
By default, only the first user (which was created during the installation) will be able to use sudo. Any users added later will not be able to use sudo unless you add them to the "admin" group.

---

### Post by bumanie on 2008-01-14
I believe you can go to System -->  Administration --> User Groups. Once in the user groups, have a look at managing groups. You should be able allow or disallow various tasks for different users.

---

### Post by Sef on 2008-01-14
> I believe you can go to System --> Administration --> User Groups. Once in the user groups, have a look at managing groups. You should be able allow or disallow various tasks for different users.

That is correct.

---

