---
title: "root login from terminal"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by chymo on 2006-09-19
I just installed ubuntu and can not access the root acount. I thought the password was the same as my current user account, but it doesn't work. I also went into user/groups admin and changed the pw for root. I'm getting "Authentication Failure. Sorry"

Is there a setting which allows root login via terminal that I'm missing?

Thanks.

---

### Post by sktx on 2006-09-19
The root user is disabled in Ubuntu for security reasons.  Anything you would want to do as root you can do with the **sudo **command... like:
```
sudo vi rootownedfile.conf
```However, when you're running a GUI program, it's advisable to use **gksudo **instead.
```
gksudo synaptic
```If you really have a need to open up a root terminal, open up an xterm or log in to the console and type:
```
sudo -s
```All of these commands will prompt you for a password, when they do they are prompting you for your user password, and not the pw for root.  In a default Ubuntu install, the root user has no password, which keeps it from logging in and helps prevent a brute-force attack from gaining access to your root user.

Note that only users who are in the group **admin** can use the **sudo** command.  This can be changed by editing your **sudoers** file.  The default setup is pretty workable, though...

---

### Post by mitch.c on 2006-09-19
> **chymo said:**
> I just installed ubuntu and can not access the root acount. I thought the password was the same as my current user account, but it doesn't work. I also went into user/groups admin and changed the pw for root. I'm getting "Authentication Failure. Sorry"

Is there a setting which allows root login via terminal that I'm missing?

Thanks.

You need to take a look at this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jISh on 2006-09-19
You shouldn't have any need to login to root account. If you want a quick fix, just sudo -i

---

### Post by robins_web on 2006-09-19
However, if for some reason you *do* wish to enable the root account, open a konsole window. At the system prompt, type *sudo passwd root*. You will be prompted for your password. This is YOUR password--the one you log in with. Then you will be prompted with *Enter new UNIX password:* This is where you enter the new password for root.

However, unless you have a special need for logging in as root, it's much better security NOT to enable the account.

---

### Post by chymo on 2006-09-19
I know you can use sudo for everything... I had another ubuntu installation on a different pc and typed su root, entered pw and I was root.  For some reason with this installation, it's not the same. Just wondering why that is.

---

### Post by chymo on 2006-09-19
I read through that doc, also did sudo -i and created root pw. Is this the only way the root acct can be activated?  If so, I guess I don't remember doig this on the other machine. I thought I just typed su and entered the same user pw. Thanks.

---

### Post by sktx on 2006-09-19
> **chymo said:**
> I know you can use sudo for everything... I had another ubuntu installation on a different pc and typed su root, entered pw and I was root.  For some reason with this installation, it's not the same. Just wondering why that is.

The default settings have been tweaked in an attempt to increase security.

---

### Post by jISh on 2006-09-19
su and sudo are different.
su is Switch User and if no account is specified will attempt to log you into the root account. Which is disabled in ubuntu.

sudo is SuperUserDO which just references the root account for authority.

---

