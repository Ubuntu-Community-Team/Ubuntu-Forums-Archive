---
title: "Quick question"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by Olly1234 on 2006-08-26
Hey all, quick question, how do you change the permissions for the root folders /usr... etc? because it says I'm not the owner! (altho I am!) thanks...

---

### Post by MrHorus on 2006-08-26
> **Olly1234 said:**
> Hey all, quick question, how do you change the permissions for the root folders /usr... etc? because it says I'm not the owner! (altho I am!) thanks...

Except your not.

Everything not owned by you is owned by root.

You don't need to change this and in fact I would STRONGLY recommend that you don't try as this can break thing and leave you open to lots of security holes as the permissions will be wrong.

---

### Post by az on 2006-08-26
> **Olly1234 said:**
> Hey all, quick question, how do you change the permissions for the root folders /usr... etc? because it says I'm not the owner! (altho I am!) thanks...

Those folders and the files in them are managed by the package manager.  You can compile and install stuff yourself, but unless you know what you are doing, don't play around there.

---

### Post by steve.horsley on 2006-08-26
MrHorus is right. Changing all the permissions so that your user is owner will leave the system unuseable and in need of reinstalling.

root is the owner, the administrator of the machine. When working outside of your home folder i.e. when doing system admin tasks, you should assume root's provoleges for a while. Do this by using **sudo** in front of the commands you issue.

For security reasons, you do not log in as root, and in fact root's account is disabled so the root cannot log in. Security reasons include the fact that when not running as root, even if you open something that contains a virus, it cannot affect the machine. 

Read this link:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

