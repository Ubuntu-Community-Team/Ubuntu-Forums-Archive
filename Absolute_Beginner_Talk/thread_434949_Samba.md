---
title: "Samba"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Typie on 2007-05-06
Hey!
I've set up Samba, and all is working fine so far, but I would like to ask this.

If I am logged in as "User1" on Windows I would like the mapped network drive to show the files for /home/samba/user1, if I'm logged in as "User2" on Windows I want it to show /home/samba/user2.

Could someone please explain how or point me in the direction of a tutorial?

Thanks!

---

### Post by MikeEvans on 2007-05-07
This is a more windows specific issue.  If your using a windows server then you should do this through group policy.  If not you need to add a script to the 'all users\startup' folder.  That will be a .bat file that looks something like this:

```
net use v: /d
net use v: \\servername\sharename sharepassword /USER:domainname\domainuser
```

now you will have to replace sharename with %username%.  For you password you can do no password, the same password for everyone, or set the password the same as the username and use %username%.

Type

```
net use ?
```

for more info or search Microsofts knowledge base

this might not work on windows vista.. not sure.

---

