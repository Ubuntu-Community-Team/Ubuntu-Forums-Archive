---
title: "Problems with 'touch /quota.user /quota.group'"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by Kephron on 2007-09-17
HI,

 I'm fairly new to Linux and I am having problems trying to set LAMP up on it.  I am faithfully following instructions from a How To Forge document.  When I try and use the command

touch /quota.user /quota.group

I am getting the following error

touch: cannot touch `/quota.user': Permission denied
touch: cannot touch `/quota.group': Permission denied

Why is this?  I am trying to run these commands as root.  I also can't run the 

chmod 600 /quota.*

command.  This is returning a similar error

chmod: changing permissions of `/quota.group': Operation not permitted
chmod: changing permissions of `/quota.user': Operation not permitted

Help?

K.

---

### Post by kellemes on 2007-09-17
I'm not into LAMP myself but maybe you should use sudo? You probably need root-privileges.
Like "sudo touch /quota.user /quota.group"

---

### Post by Majorix on 2007-09-17
Are you sure you are running them as root? Because if you were you wouldn't get those errors. As suggested use "sudo" infront of the command.

---

### Post by Kephron on 2007-09-18
The command is being attempted as the root user.   Open a terminal window.  type su.  type in root password.  You are now logged in as the root user (I believe).
The result of using sudo in front of the command either as root or as my own user gives the same error as running it as root without sudo (although my own user account prompts me for a password first)

Tring to run the command (sans sudo) using my normal user account gives the same error as trying it as root (see previous post).

K.

---

### Post by DieselGuy104 on 2008-03-20
Anyone ever find a solution to this? I am having the same "permissions denied" problem while logged in as root. I also get the same error when running command

```
chmod 600 /quota.*
```

Any suggestions?

p.s. I am trying to follow "The Perfect Setup" on howtoforge.com for Ubuntu 7.04

---

