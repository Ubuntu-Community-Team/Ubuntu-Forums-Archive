---
title: "Samba Problems"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by tc3racer on 2006-09-19
im having a real bad time with samba i cannot access it on my windows xp machine as every time im asked for a password and username i do not know whta i put in i tried to add a user but get the following

root@xxxxxxx:~# smbpasswd -a linux
New SMB password:
Retype new SMB password:
Failed to initialise SAM_ACCOUNT for user linux. Does this user exist in the UNIX password database ?
Failed to modify password entry for user linux

Note Root @ is in x's so it does not show the server name

---

### Post by kidders on 2006-09-19
Hi there,

Your error is fairly self-explanatory:

> Does this user exist in the UNIX password database?

If you don't keep your samba & unix usernames consistent, samba would have no way of mapping user privileges between them without help.

---

### Post by tc3racer on 2006-09-20
Hi how do i find out if the user is not in the unix password database. im a newbie to ubuntu linux and not a 100% sure how you install programs yet and how to use terminal

---

### Post by kidders on 2006-09-20
No problem :-)

Basically, when a remote user does something over samba, like delete/create a file, your system needs some way of deciding whether that user should be allowed to do so. It does that by mapping the samba (Windows) username to a real Linux one. Some mappings like "Administrator => root" are created for you automatically, but the handiest thing to do for beginners is forget about all that for a while, and use "real" user accounts instead.

You can create a new account on your system with the **useradd** command ... check out its man page first though!

Once that's done, samba will be happy to let you in, using that username. The samba & Linux passwords don't have to be the same however, so that's why people use **smbpasswd** to set samba's version of that user's password a second time.

If you're not too hot with the command line, there is probably a pretty graphical utility on your system for adding new users. In either case though, it's important to stop and think for a moment before doing anything that you find yourself typing "sudo" before.

I hope that's more helpful :-)

**Edit:** Incidentally, installing programs is a snap. Ubuntu provides a nice package manager that handles lots of horribly complicated messing for you, such as:

[LIST]
[*]Whether your computer's existing software will play nice with something new you want to install
[*]Whether you need to put additional software/system libraries on first to make your new app work (... or maybe take something off!)
[*]Automatic detection of security updates or new releases
[/LIST]

All you need to know is the system's name for the app you want. For instance, you can install samba by typing **sudo apt-get install samba** ... Ubuntu does the rest.

---

### Post by sYs^ on 2006-09-22
Set in /etc/samba/smb.conf

```
security = share
```

---

### Post by fjseymour on 2006-09-23
> **sYs^ said:**
> Set in /etc/samba/smb.conf

```
security = share
```

Thank you.  I had been having the same problem.  Your "security = share" did the trick for me.  I knew I would eventually find the solution.  Most of the other posts dealing with this had the default "security = user" in their smb.conf examples.

---

### Post by martinbures on 2006-09-23
Here is a odd question.

How do I make SAMBA work as well with my linux laptop as it does with my mac laptop?  The mac and the linux box talk easily and give access to each other with no problems.  However, with my linux laptop, when I try to log into my linux pc, it won't let me.  I installed SAMBA, enabled sharing.  What else do I need to do?  Why does it let the mac laptop do more than the linux laptop?  Both the linux laptop and the linux desktop were running Dapper.

---

### Post by kidders on 2006-09-24
Strange.

Could you provide some more detail about your problem? "It won't let me" doesn't give us much to go on :-(

This may be a silly question, but are you certain you're using the correct usernames/passwords in all cases?

---

### Post by tc3racer on 2006-09-25
thanks for you help guys found the problem  using an application called web min found that for some reason the account had been disabled.  thanks for you help anyway

---

