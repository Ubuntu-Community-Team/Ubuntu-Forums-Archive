---
title: "Giving root permission to a user"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by ejoftiduttu on 2008-02-04
Can any one tell me how to give root power to users

---

### Post by jordanmthomas on 2008-02-04
sudo is what you'll want to use.
gksudo if you're going to run graphical apps.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by kpkeerthi on 2008-02-04
> Open a Root Terminal (sudo -su) and type visudo 
> Add the following ```
user ALL=(ALL) ALL
``` to the end of the file
> Save and exit.

**Note: **Replace **user** with your actual username

---

### Post by p_quarles on 2008-02-04
The quickest and easiest way to do this in Ubuntu:
```
sudo adduser *username* admin
```

---

### Post by ejoftiduttu on 2008-02-04
NO, i want to give auser the full power of root...How can i do that

---

### Post by p_quarles on 2008-02-04
Sudo does give a user full root power.

If you want a root shell, type:
```
sudo -i
```
Be careful when doing this, though.

---

### Post by hyperair on 2008-02-04
Basically you want to be able to do everything as root? Only one way to do that is to sign in as root. First enable the root password (in System->Administration->Users and Groups, set the root password to something you know). Then, enable superuser login in GDM (System->Administration->Login Window->Security->Allow local system administrator login).

The above is highly unadvisable as anything you do can affect the whole system's files. But that will achieve what you are looking for. On a slightly less dangerous route, you could install nautilus-gksu from Synaptic. That will allow you to right click on a file and open it as root.

---

### Post by jordanmthomas on 2008-02-04
Wouldn't adding the user to the group **root** give them lots of permission? Better yet, change your UID to 0!
(Yes, the idea makes me shudder as well..)

---

### Post by hyper_ch on 2008-02-04
are you sure you really want to make him root?

---

### Post by hyperair on 2008-02-04
@jordanmthomas: Yes, but often not enough. You probably know by now that permissions on *nix is divided into three, User, Group, and Others. User permissions applies only to the owner. Group permissions applies to the group that owns it. Others permissions apply to users who are not in the group that own the file and also don't own the file. The root user is able to access all files despite of the permissions specified. Putting him in the group root only grants him access to those files which are readable/writable by the group root, which doesn't include all files.

---

### Post by jordanmthomas on 2008-02-04
> **hyperair said:**
> @jordanmthomas: Yes, but often not enough. You probably know by now that permissions on *nix is divided into three, User, Group, and Others. User permissions applies only to the owner. Group permissions applies to the group that owns it. Others permissions apply to users who are not in the group that own the file and also don't own the file. The root user is able to access all files despite of the permissions specified. Putting him in the group root only grants him access to those files which are readable/writable by the group root, which doesn't include all files.

hence setting UID to 0.  :lolflag:

---

### Post by hyperair on 2008-02-04
Nope, only the GID.

---

### Post by jordanmthomas on 2008-02-04
> **hyperair said:**
> Nope, only the GID.

I mean set the user's UID to 0, then he will be root essentially.  (Honestly I don't even know if you can, since root's already a user on the system)
also forgive me if I don't make sense, it's 5:30 am and I should get to sleep.

---

### Post by p_quarles on 2008-02-04
Giving a normal user full root privileges is not a good idea, for a whole host of reasons. Basically, you shouldn't do it unless you understand the consequences for security and system stability. This is simply not how any *nix system was designed to operate.

---

