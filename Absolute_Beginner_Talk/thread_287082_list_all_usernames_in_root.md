---
title: "list all usernames in root?"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by poisonborz on 2006-10-28
Installed Edgy... but can't use it. As far as I remember, I just gave 'ab' both for login/pass (it was meant to be just a test system), a few days later (yeah, I know it's lame, installed, but didnt had the time to run) when I treid to log in, it failed. I know I could change the pass in recovery, but apparently user 'ab' doesn't exist... and without a main username, I can't change it

---

### Post by paulmilliken on 2006-10-28
Try booting from a live cd (any distro) and do "ls /home" at the command line to see a list of users' home folders (and consequently a list of users).

Paul

---

### Post by Bachstelze on 2006-10-28
```
cat /etc/passwd | grep 1000
```

no need to even be root ;)

---

### Post by poisonborz on 2006-10-28
what a simple idea...thanks :)

...turned out, that the username is "oem"... I selected OEM install, but does this mean main user name is automatically "oem"? Far as I remember, I just gave "ab" to it, is this too small, and did the name change to "oem" without warning...?

---

### Post by taurus on 2006-10-28
You have to log in using oem and the password that you have created for oem during the installing process.  Then, you need to run a command, oem-config-prepare, to create a new user and it will automatically erase oem from your system...  I guess you picked the second option from the alternate CD since the first option is to install it using text base (at least for Edgy).  Just installed it using an alternate CD on one of my computers at work this afternoon.

---

