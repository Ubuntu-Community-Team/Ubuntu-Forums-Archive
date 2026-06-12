---
title: "I hate using sudo [Resolved]"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by benutne on 2007-03-21
I'm sure there are countless people complaining about the lack of a root user, but I thought I'd toss in my $.02.  I like the idea of not having a root user.  That said, I hate having to use sudo to do all of my administration tasks.  Is there any way to create a user who is not called root be a member of the root group using Ubuntu?  I plan on using my normal user account for everyday tasks, and when I need to change a setting, log in as this "root" user.  

Any help?  And please do not give me a million other ways to accomplish the same task.  I am comfortable doing things this way (albeit in a Windows environment) and would like to continue doing so.

---

### Post by sunexplodes on 2007-03-21
People will cry afoul of this, but it's quite simple to run as root in Ubuntu. Just go into System>Administration>Users and set a root password, and then into System>Administration>Login Window, go to the security tab, and then check the box that says "Allow system administrator login".

---

### Post by aysiu on 2007-03-21
Create a launcher for the command ```
gksudo nautilus
``` When you want to "log in as root," just click that launcher.

---

### Post by cowlip on 2007-03-21
Is there any way that you can use gksudo to get into these tasks?  Like adding gksudo nautilus, gksudo <whatever> into your current user's menu?  Sudo has a waiting time of 5 minutes before asking for your password as well..

BTW I remember asking how not to be root on a Linux forum a few years ago and I got screamed at so I wimped out ;)  So funny how much friendlier forums are these days

---

### Post by aysiu on 2007-03-21
This link has everything you need to know about root and sudo. It even includes a section called **Going back to a traditional root account**

Read it. Learn something.

[https://help.ubuntu.com/community/RootSudohttps://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudohttps://help.ubuntu.com/community/RootSudo)

---

### Post by bodhi.zazen on 2007-03-21
> **benutne said:**
> I'm sure there are countless people complaining about the lack of a root user, but I thought I'd toss in my $.02.  I like the idea of not having a root user.  That said, I hate having to use sudo to do all of my administration tasks.  Is there any way to create a user who is not called root be a member of the root group using Ubuntu?  I plan on using my normal user account for everyday tasks, and when I need to change a setting, log in as this "root" user.  

Any help?  And please do not give me a million other ways to accomplish the same task.  I am comfortable doing things this way (albeit in a Windows environment) and would like to continue doing so.

You can become root in a terminal with :

```
sudo -i
```

If you like, you can then set a root password :

```
passwd
```

Then disable (or not) sudo

```
visudo
```

comment out (add a # at the front) of this line :

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

Like this :

> # Members of the admin group may gain root privileges
# %admin ALL=(ALL) ALL

Now to become root , in a terminal type :

```
su
```

Enter you new root password.

========

Your other option is to create a second user. Do not add the second user to the admin group.

HTH

---

### Post by benutne on 2007-03-21
Thanks for the help everyone.  I really appreciate the direct answers.

---

