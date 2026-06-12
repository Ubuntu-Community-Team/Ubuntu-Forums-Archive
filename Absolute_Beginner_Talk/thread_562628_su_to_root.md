---
title: "su to root???"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by NetDoc on 2007-09-29
When I installed ubuntu, I noticed that it asked for a password ONLY for the user I set up: it never asked for a root password. When I opened up a terminal, I tried to su to root and no password worked (go figure). I started the installation process and got to the point of doing the actual install and again, it never asked me to set the root password. Is root replaced by the user I created? Inquiring minds want to gnow! :)

---

### Post by llamakc on 2007-09-29
Ubuntu doesn't enable root by default. If you're familiar enough with Linux you can easily enable it. Search for precisely that question: howto enable root on ubuntu.

---

### Post by nine01a on 2007-09-29
I'm pretty sure that the root password is randomized by default. You can use `sudo su -` to get to a root shell if needed. (the - includes the root "profile.")

You could `sudo su -` then `passwd` to change the root password if you wanted.

Hope that helps.

---

### Post by llamakc on 2007-09-29
It's not randomized, it is not enabled by default.

The way to enable it is:

sudo passwd root

(you enter your password for the sudo command)

and then enter & re-enter the root password that you want to set.

Now you can su to root.

---

### Post by bodhi.zazen on 2007-09-29
> **nine01a said:**
> I'm pretty sure that the root password is randomized by default.

This is a common mis-perception.

By default the root account is locked and sudo is patched to allow this.

> You can use `sudo su -` to get to a root shell if needed. (the - includes the root "profile.")

You could `sudo su -` then `passwd` to change the root password if you wanted.

Hope that helps.

sudo -i is the preferred method.

'sudo su -' works, but this (su -) is used to become root on systems without sudo.

I know, I know it is nitpicking , but gotta teach 'em right.

_Note_: It is tempting to set a root password, especially if you are not accustomed to sudo in Ubuntu. After a while most of us realize that there is no need to do so, and the locking of root is part of the way Ubuntu handles security. Again, not that this is the only way to handle security, but just a caution to new users who may not understand the how and why of sudo in Ubuntu.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

_Note 2_: If you set a root password and want to disable the root account, just ```
sudo passwd -l root
```

---

### Post by llamakc on 2007-09-29
I always forget about `sudo -i`. I'm gonna set an alias for it. Thanks bodhi.

---

### Post by nine01a on 2007-09-29
> **bodhi.zazen said:**
> This is a common mis-perception.

/etc/shadow shows a "!" in the password field as I found out after posting my lies. Didn't know about the [FONT="Courier New"]sudo -i[/FONT] either. *changes his ways*

---

### Post by bodhi.zazen on 2007-09-29
> **llamakc said:**
> I always forget about `sudo -i`. I'm gonna set an alias for it. Thanks bodhi.

> **nine01a said:**
> /etc/shadow shows a "!" in the password field as I found out after posting my lies. Didn't know about the [FONT="Courier New"]sudo -i[/FONT] either. *changes his ways*

:lolflag:

Thanks you two :redface:

/bodhi.zazen is a reformed su - 'er

---

### Post by NetDoc on 2007-09-29
Whoa... two quick replies and both of them solutions! I am way impressed with this forum! Consider it bookmarked, and many, many thanks!

---

