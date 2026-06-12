---
title: "Using sudo -u"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by wnwek on 2007-12-13
Sorry if my question has been repeated, but here is what is happening on my computer.

A few days earlier, I created a new account for my sister ("guest") on my laptop, but I did not give the account administrator privileges. Now, once she logged in, she wanted to install flash in firefox, which I figured I could do, if I could start it as me ("vivek"). 

So I thought the command to do that from the terminal is:

```
guest@wnwek> sudo -u vivek firefox
```

But that doesn't seem to work. I went through the sudo manual and it is supposed to work. What am I doing wrong?

---

### Post by subs on 2007-12-13
an excerpt from the sudo manual....

> Note that if the targetpw Defaults option is set (see sudo&#8208;ers(5)) it is not possible to run commands with a uid not listed in the password database

have u checked this out???

---

### Post by wnwek on 2007-12-16
What does this mean? Where do I see whether that option is set or not? Besides, my /etc/sudoers file has the admin group as sudoer, which is the standard configuration, ("vivek") is part of that group.

---

### Post by wnwek on 2007-12-16
Excerpt from the sudoers manual:

>  targetpw    If set, sudo will prompt for the password of the user spec&#8208;
                   ified by the -u flag (defaults to root) instead of the
                   password of the invoking user.  Note that this precludes
                   the use of a uid not listed in the passwd database as an
                   argument to the -u flag.  This flag is off by default.

I got the relevant paragraph. Let me see if I got it.

---

### Post by wnwek on 2007-12-16
What I get from the previous quoted paragraph from sudoers manual, is that if you execute

```
sudo -u vivek cat /etc/sudoers
```

and if the targetpw is set to be off, then it should ask me for root's password. I went through the sudoer's file and from what I can figure out, this option is set to be off. But it still asks me for "guest"'s password. 

I even set a password for root, and it is not accepting it. But when I type in "guest"'s password it accepts it, but nothing happens (nothing should, which is good). But I can't seem to do any admin work when another user is logged, unless I su into root.

---

### Post by thelatinist on 2007-12-16
Why not log into your account and install flash from there?

---

### Post by wnwek on 2007-12-17
1.) If you mean log out of Ubuntu, and log in as me, and then install flash, then that would not solve my purpose, since it is some sort of user local installation. 

2.) If you mean su into my username and then do it, yeah I could do that, but isn't sudo -u supposed to do the same thing? That was what I was wondering. Actually, I am trying to figure how it works.., I did manage to install flash :)

---

### Post by spiderbatdad on 2007-12-17
what i see in ```
man sudo
``` is ```
sudo -HPSb -u username
```

---

