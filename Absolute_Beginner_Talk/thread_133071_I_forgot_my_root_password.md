---
title: "I forgot my root password"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by YellowHat on 2006-02-19
:(  I thought I entered my password at installation but now it doesn't seem to be working at all anymore. I'm talking about when I boot up and I go to the soothing screen with the background. Basically I forgot my password and username. 

Is there a method of password recovery?

---

### Post by kaamos on 2006-02-19
Sound like you forgot your user passwd and not root?

When booting the machine, enter grubs menu and choose "recovery mode". This will get you a root shell. If you really can't remember your username, type
```
more /etc/passwd
```
and look it up. Then type
```
passwd username
```
replacing "username" with your username. Once done, type
```
shutdown -r now
```
and let ubuntu boot normally.

---

### Post by tadashi on 2006-02-19
It is your password.  It took me a bit to get used to it but I think Ubuntu makes the root password the same as your acct.  Other Linux installations asked me for an admin pass and acct pass.  I think I like it better this way since I am the only user on this laptop.

---

