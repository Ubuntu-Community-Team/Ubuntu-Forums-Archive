---
title: "terminal commands"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by saltscar on 2006-01-18
When Ienter a command in the terminal, it hen asks for a passwod.  I try to enter my password but it will not type in - my keyboard does not respond.  Any help please?

---

### Post by chris.olsen on 2006-01-18
I just don't think that any chars are being displayed on the screen.  Just type in the root password and see if it works

---

### Post by earobinson on 2006-01-18
chris.olsen is correct for security reasons when you type your password in the terminal '*' is not displayed.

---

### Post by saltscar on 2006-01-18
As a linux novice, what is a root password?

---

### Post by christhemonkey on 2006-01-18
the password that lets someone log on as an administrator.  So they can edit or delete (most) any files they like.  Be careful when logged in as root not to accidentally do something stupid:D lol.
It is used from command line when typing commands with the prefix "sudo ".

---

### Post by 23meg on 2006-01-18
> It is used from command line when typing commands with the prefix "sudo ".The password you're asked for when you use sudo **isn't** the root password; it's your user password. The root account is disabled by default in Ubuntu. 

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by earobinson on 2006-01-18
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) <-good info

Long and short of it:
the root users is like the 'administrator' as christhemonkey said, so the root password is like the 'administrator' password. and like christhemonkey said is very dangrous because you can deleat anything.

Ubuntu by default disables the root account and instead they use sudo, this lets a user gain root axcess for only one command, and is the same password as the password of the account you made during the install.

It is highly recomended by the ubuntu dev team that you use sudo and never root (su)

EDIT: 23megs posted it first and probaly better lol

---

### Post by christhemonkey on 2006-01-18
> **23meg]The password you're asked for when you use sudo **isn't** the root password said:**
> http://wiki.ubuntu.com/RootSudo[/url]
 Sorry my bad:D

---

### Post by saltscar on 2006-01-18
Many thanks folks.  It worked fine.  I am learnring the hard way but getting there!!:

---

### Post by earobinson on 2006-01-18
Thats how everyone learns

@christhemonkey not a problem thats how we all learn.

---

