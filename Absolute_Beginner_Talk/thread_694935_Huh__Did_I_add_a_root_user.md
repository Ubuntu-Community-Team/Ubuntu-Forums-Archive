---
title: "Huh?  Did I add a root user?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-02-12
I tried installing mythbuntu...

but when I do...
nibbles@nibbles-desktop:~$ grep mythtv: /etc/group
mythtv:x:121:root,nibbles
nibbles@nibbles-desktop:~$ 


So there's this root user...  is this bad?  I thought ubuntu didn't want a root user...

problem?  I've never set up a root user or password...  would this make my sshd insecure?

---

### Post by shad0w_walker on 2008-02-12
Ubuntu has a root account by default, however it isn't given a password (Essentially disabled) so this is normal and shouldn't be a problem.

---

### Post by emarkd on 2008-02-12
You can't not have a root user.  Ubuntu just doesn't have a password set for the root user, so not only can you not log in as root, nobody can 'crack' the account either.

---

### Post by prabbit237 on 2008-02-13
> **joesmith1234 said:**
> I tried installing mythbuntu...

but when I do...
nibbles@nibbles-desktop:~$ grep mythtv: /etc/group
mythtv:x:121:root,nibbles
nibbles@nibbles-desktop:~$ 

So there's this root user...  is this bad?  I thought ubuntu didn't want a root user...

problem?  I've never set up a root user or password...  would this make my sshd insecure?

To answer the question not quite asked/answered, that user isn't the root user but is part of the same group as root. Files, directories, etc. have 3 types of permission: owner, group and "everyone else." So you can set it so that the owner can read the file, write to it, execute it, etc. and anyone in the same group as the owner can read it and execute it but anyone else can only execute it (or various combinations there-of.) This user (mythtv) is in the "root" group and also in the "nibbles" group and thus can do anything anyone in those groups can do. But that doesn't give the user full root access.

See [http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html) for some more info on how groups work.

---

### Post by jordanmthomas on 2008-02-13
> **prabbit237 said:**
>  This user (mythtv) is in the "root" group and also in the "nibbles" group and thus can do anything anyone in those groups can do


Actually, it means that root and nibbles are in the mythtv group, not vice-versa

---

### Post by prabbit237 on 2008-02-13
> **jordanmthomas said:**
> Actually, it means that root and nibbles are in the mythtv group, not vice-versa

You're right, I was getting it reversed<sigh> Typing faster than my brain was working.

---

