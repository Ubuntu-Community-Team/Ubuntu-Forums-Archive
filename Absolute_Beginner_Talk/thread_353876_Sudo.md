---
title: "Sudo"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by ColinP on 2007-02-05
I have installed Ubutu but, at no stage was I asked to enter a password for administrator privilages !      Version used 6.06.1  .  The same result was seen when using a downloaded version.   Obviously, there something I am not unaware of.  Being a beginner with Linux,  I would be grateful for some advice.

---

### Post by jvc26 on 2007-02-05
Have a look at:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
You will only be asked for the password when trying to install or edit system files, all functions within your /home directory are possible as you have permissions to read/write/edit etc.
Il

---

### Post by Spr0k3t on 2007-02-05
Try using the same password you setup for your account that you currently use to log into the Linux environment.  Unless you've changed some settings, it should be the same.

---

### Post by Ryan450 on 2007-02-05
I know when ubuntu gets installed its root password is randomized, which is a very annoying thing that drives me crazy to no end. 

easiest thing to get around this and use the root account like you normally would is simple. just go into your terminal type in 

sudo passwd root

it will then prompt for a new password and away you go. I'll never understand the reasoning behind ubuntu's default sudo setup though. I dont like the idea of the first user account having administrative privledges over everything via sudo.

---

### Post by ColinP on 2007-02-05
Many thanks for your advice ; all is OK now !

---

### Post by jvc26 on 2007-02-05
> **Ryan450 said:**
> I dont like the idea of the first user account having administrative privledges over everything via sudo.

Ubuntu requires sudo and your user password to do anything which is a security measure to stop random things being able to access and edit system files like viruses etc. Its a straightforward process to put in your password each time.

Interested: Why don't you like the idea of the first user having admin privileges via sudo?
Il

---

### Post by Ryan450 on 2007-02-05
simple, I set up ubuntu on a friends computer and his entire family just uses the user/pass. 

someone went in and mucked up networking settings with the sudo privledges via the gui, not entirely knowing what they were doing.

---

