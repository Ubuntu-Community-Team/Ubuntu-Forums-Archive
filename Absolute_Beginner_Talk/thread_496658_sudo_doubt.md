---
title: "sudo doubt"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by desijays on 2007-07-09
Something weird happened

ubuntu@ubuntu$:su <enter>
password:            ( i entered the only password my installation of feisty asked me for )

wrong password
Sorry!

ubuntu@ubuntu$:sudo su
password:            ( it asked me for the password again and i gave the same password i typed bfore)

root@ubuntu#:

Any idea whats happening? or is this supposed to be normal?

---

### Post by Nekiruhs on 2007-07-09
Its normal. However sudo is recommended for operations requiring root privelages.

---

### Post by p_quarles on 2007-07-09
I agree with the above on using sudo rather than su.

Just a quick explanation f what happened, though: during the normal installation process of Ubuntu, it never gives you the option of setting the root password. When you typed "su" by itself, the system was looking for you to give it the root password (which hasn't been set). "sudo" on the other hand gives the non-root user temporary root privileges (15 minutes). It's pretty easy to set the root password if you want to, but using sudo is more secure.

---

### Post by aysiu on 2007-07-09
Of course it's normal.

*su* means *switch user*. If you don't specify a user, it will assume you mean the root user and ask for the root password. There is, for all practical purposes, no root password set in Ubuntu, so when you're asked for the root password, it will always say your password is wrong.

*sudo su* gives you a root shell but using *sudo*, which allows you (provided you are in the *admin* group) to temporarily escalate your privileges to a root level, but it asks for your username.

More details here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by meborc on 2007-07-09
> **p_quarles said:**
> I...during the normal installation process of Ubuntu, it never gives you the option of setting the root password. When you typed "su" by itself, the system was looking for you to give it the root password (which hasn't been set)...

actually, during the installation, the root password IS set, but it is a random mix of letters and numbers...

other then that - i totally agree... using sudo is much more safe... :D

---

### Post by desijays on 2007-07-09
> **aysiu said:**
> Of course it's normal.

*sudo su* gives you a root shell but using *sudo*, which allows you (provided you are in the *admin* group) to temporarily escalate your privileges to a root level, but it asks for your username.



it didn't ask me for my username or anything. it asked me for just the password. after it checked in right, it let me be root. ofcourse i used exit soon after.

didn't wanna play ubuntu in GOD mode ;)

---

### Post by aysiu on 2007-07-09
Sorry. I meant to type *password* instead of *username*

---

