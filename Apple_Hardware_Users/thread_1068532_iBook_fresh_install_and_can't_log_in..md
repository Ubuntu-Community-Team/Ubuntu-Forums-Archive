---
title: "iBook fresh install and can't log in."
date: 2009-02-13
forum: Apple Hardware Users
---

### Post by ant2ne on 2009-02-13
I manged to install xubuntu on my iBook. 

It boots to the login screen in which I put the credentials that I entered when doing the install. It acts like it is logging me in, but then a window pops up saying "You are required to change your password immediately (root enforced)" I then click "OK" and I'm back at the login screen.

If I Cntl+Alt+F2 to get to a terminal, I'm presented with a login: I enter my credentials and it says "You are required to change your password immediatly (root enforced)", next line "Authentication Failure", and asks me to log in again.

At first I thought 'dang, I messed up my password during the install'. So I did the install again. I know I got it right the second time. I typed it very slow and deliberate.

Now what?

---

### Post by ant2ne on 2009-02-13
3rd time with a simple password and user name. No way I messed that up.

---

### Post by cyberdork33 on 2009-02-13
boot into recovery mode where you should be able to get to a root terminal. You can then change the user password by using the command:
```
passwd *username*
```

It will then prompt you to type the new password in twice, and your password will be changed, then you can try to login normally again.

---

### Post by ant2ne on 2009-02-13
> **cyberdork33 said:**
> boot into recovery mode where you should be able to get to a root terminal. You can then change the user password by using the command:
```
passwd *username*
```

It will then prompt you to type the new password in twice, and your password will be changed, then you can try to login normally again.Booted CD. Typed "rescue" as the boot option. Got to a rescue prompt. Executed passwd ant and it prompted me for the password twice. And then spit back "passwd: password updated successfully". Then I typed exit and selected reboot the system. 

Still the exact same problem. I don't think this is an issue with my user name and password. There is some other bug that I've encountered.

---

### Post by ant2ne on 2009-02-13
if i enter the user name, and an incorrect password, it never says "You are required to change your password immediately (root enforced)"  It just says "login incorrect" It is like it authenticates me, but kicks me out.

---

### Post by ant2ne on 2009-02-13
Found a posilble date bug. I logged in with rescue again and executed a date command with the current date. no effect

This is really driving me nuts.

---

### Post by mkvnmtr on 2009-02-13
I do't believe cyber dork was saying to boot into the live disk. I believe he meant to boot your system on your computer.

---

### Post by cyberdork33 on 2009-02-13
> **mkvnmtr said:**
> I do't believe cyber dork was saying to boot into the live disk. I believe he meant to boot your system on your computer.
yep. not the cd, the installed system. If you do it from the CD, then you are attempting to change a password of a user on the LiveCD environment. that is not what you want.

---

### Post by ant2ne on 2009-02-13
> **mkvnmtr said:**
> I do't believe cyber dork was saying to boot into the live disk. I believe he meant to boot your system on your computer.
Ok, I'm an idiot. How do I do that? iBook uses yaboot, not grub.

---

### Post by ant2ne on 2009-02-14
I guess 4th time is the charm. I re-installed. This time I got in. I don't know why. 

I have a different set of problems. But at least I can log in. I'll open a new thread for my new problem and reference this thread.

---

