---
title: "Multiple Users"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by Loft on 2006-06-30
Just a quick question about multiple users and sudo'ing.

Basically, I want to setup 2 other accounts on Ubuntu, other than mine, but would like to get a better overview of dealing with multiple users anyway.  All will be different accounts on the same computer.

Now say Person A installs Ubuntu (that person being me), they have access to the sudo command yeah?  So Person A will not only have their own /home folder, but be able to use sudo for updates etc.  That bit I'm fine with.

Now if I add a user, Person B, they have their own /home folder, but do are they able to use the sudo command?  If so, how? Using their own password, or the sudo password (which I assume is the same as Person A's password?).  I figure from the messing about I've done, this isn't the case by default? Am I right?

Now say I want another user, Person C, once again they get their own /home folder, but say I do actually want them to be able to use the sudo command.  Would I have to set this up?  And if so, would the password be the sudo password (Person A's password)?

Thanks in advance.

---

### Post by IYY on 2006-06-30
By default, a newly added user will not have the administrator rights. Do give him/her these rights, just add the username to the admin group. This can be done with the gui, but I usually just add the name to /etc/groups.

For example,

```
admin:x:106:firstuser,seconduser
```

---

