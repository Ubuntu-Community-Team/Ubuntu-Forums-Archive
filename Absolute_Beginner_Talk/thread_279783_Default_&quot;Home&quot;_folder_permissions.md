---
title: "Default &quot;Home&quot; folder permissions"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by ZiRo on 2006-10-18
I'm having trouble finding a way to set the _default_ folder permissions of a new user.

I don't want users' to be able to _defaultly_ access eachothers home folder.

E.G. How can I _automatically_ set the permissions of a newly created user's home user folder to be exec/read/write by Owner only?

Thanks for help,

---

### Post by bswilson on 2006-10-18
Set the permissions via the Terminal.

```
$ sudo chmod -R 700 /home/username
```

Obviously, substitute username for the real user's id.  The -R flag does this recursively for all subdirectories.

---

### Post by ZiRo on 2006-10-18
I'm not after that. I'm sorry I didn't make myself clear.

I want to automate this. So when a new user is created, the permissions are automatically set.

---

### Post by aidanr on 2006-10-18
sudo chmod -R 700 /home/user1
sudo chmod -R 700 /home/user2

edit:// beat to it
edit2:// i think you have to change /etc/skel or something, not at all sure about that though

---

### Post by ZiRo on 2006-10-18
> **aidanr said:**
> edit2:// i think you have to change /etc/skel or something, not at all sure about that though

I tried editing the permissions of /etc/skel - no joy.

---

### Post by christofer.c.bell on 2006-10-18
[FONT="Courier New"]# **sudo dpkg-reconfigure adduser**[/FONT]

A[FONT="Courier New"]dduser
-------

Normally, home directories can be viewed by all users on the system. If you wantto increase the security/privacy on your system, you might want your home directories only readable by the user. If you are unsure, enable system wide readable home directories.

This will only affect home directories of users added with the adduser program later.

Do you want system wide readable home directories? [/FONT]

(Answer "No", hit Enter, and that's it.  You will need to set existing directories in /home to 700, but everything you create later should have correct permissions assuming you are using the adduser utility.)

---

### Post by ZiRo on 2006-10-18
I tried this, however I am not having success with it. I'll try some more..

EDIT: When I use the terminal, it functions correctly. However using the application "Add Users and Groups", the rules are not set as to only allow access to the owner..

---

### Post by christofer.c.bell on 2006-10-18
Well, I don't know what to tell you then beyond don't follow any of the advice that tells you to use "chmod -R".  You're wanting to protect user files from other users, not mess with the files themselves.

$ cd /home ; sudo chmod 700 *

... is all you need.

---

### Post by ZiRo on 2006-10-18
> **christofer.c.bell said:**
> Well, I don't know what to tell you then beyond don't follow any of the advice that tells you to use "chmod -R".  You're wanting to protect user files from other users, not mess with the files themselves.

$ cd /home ; sudo chmod 700 *

... is all you need.

Thanks, I'll carry on looking to resolve this issue. Obviously it is much nicer to use the little user interface than the terminal...

---

### Post by ZiRo on 2006-10-18
i'm fairly annoyed by this issue, i'm tempted to post it elsewhere, any objections?

---

### Post by PriceChild on 2006-10-18
> **ZiRo said:**
> i'm fairly annoyed by this issue, i'm tempted to post it elsewhere, any objections?On another site - fine... but if someone knows a solution here they'll post it in this topic ;)

be patient :)

---

### Post by CatKiller on 2006-10-18
> **ZiRo said:**
> EDIT: When I use the terminal, it functions correctly. However using the application "Add Users and Groups", the rules are not set as to only allow access to the owner..

I believe that the graphical tool uses **useradd** rather than **adduser**. I don't know how to change the default permissions with useradd.

---

### Post by ZiRo on 2006-10-19
Thanks, I'm still trying to solve this problem.

---

