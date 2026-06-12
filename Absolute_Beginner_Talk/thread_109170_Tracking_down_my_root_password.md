---
title: "Tracking down my root password"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by loninappleton on 2005-12-28
I just installed Dapper Drake and I'm in trouble already:
I thought I put in my usual p-wd and now the system is refusing me entry to root.

How can this be painlessly fixed?


How do I avoid it in the future?

---

### Post by stuporglue on 2005-12-28
The installer doesn't create a password for root by default. It uses "sudo" instead for one time execution of commands as super-user. To get a root shell, you can do "sudo su" and type your user password.

---

### Post by dueY on 2005-12-28
If you haven't made a password yet you can type
sudo passwd root
to make a password for your root.

---

### Post by loninappleton on 2005-12-28
[QUOTE=stuporglue]The installer doesn't create a password for root by default. It uses "sudo" instead for one time execution of commands as super-user. To get a root shell, you can do "sudo su" and type your user password.[/QUOTE]


Oh ok.  and I can do that from the average terminal
window?

So [user]#sudo su ******


and that does it?  Does it have to be done all the time?

What's the permanent fix to all the passwordings?

---

### Post by dueY on 2005-12-28
[QUOTE=loninappleton]Oh ok.  and I can do that from the average terminal
window?

So [user]#sudo su ******


and that does it?  Does it have to be done all the time?

What's the permanent fix to all the passwordings?[/QUOTE]

The passwords are there to serve and protect!

---

### Post by Madpilot on 2005-12-28
Ubuntu is set up to use "sudo", not root.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) for further reading.

---

### Post by Masteroc on 2005-12-28
Yes, just go to your normal terminal window and type 

```
suudo su
```

it wil ask for your password. you should have set this up at installation.

Then type 

```
sudo passwd root
```

and that would be your root password.

There is no way to get rid of ubuntu always asking for password.

This helps you not do anything that you might regret.

---

