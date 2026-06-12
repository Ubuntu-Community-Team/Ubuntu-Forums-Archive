---
title: "Installing through terminal (Sudo Apt)"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by ISC on 2006-08-14
Hi all. 

When I try to install an app through Terminal or konsole, using a line such as:

sudo apt-get update

I get prompted for my root password, but then I am not allowed to enter it, the keyboard is frozen, except I can press 'return'. 

Also I am not allowed to log in as 'root'  but can view the system files with my standard user account when prompted for the 'root' password.

Any help is appreciated.

Many thanks

Ian

---

### Post by jwd45244 on 2006-08-14
use your regular password

---

### Post by earobinson on 2006-08-14
ubuntu has no root password for the sudo command use the password of the account you made during install

---

### Post by PriceChild on 2006-08-14
Asterisks (or any other feedback) will not appear... just type your password in and press enter.

It is being entered really :)

---

### Post by ISC on 2006-08-14
Thanks for the advice. But the keyboard is frozen and I can enter nothing, although the same line will work with 'gksudo'.

---

### Post by aysiu on 2006-08-14
Your keyboard isn't frozen. You will just get no visible feedback when you're entering your password. Enter your password anyway and hit **Enter** when you're done.

[It's a known problem, but the developers think it's too complicated to fix](http://www.ubuntuforums.org/showthread.php?t=214393).

---

### Post by sean_ on 2006-08-14
> **ISC said:**
> Hi all. 

When I try to install an app through Terminal or konsole, using a line such as:

sudo apt-get update

I get prompted for my root password, but then I am not allowed to enter it, the keyboard is frozen, except I can press 'return'. 

Also I am not allowed to log in as 'root'  but can view the system files with my standard user account when prompted for the 'root' password.

Any help is appreciated.

Many thanks

Ian

It's not frozen. It doesn't show the stars or text, just type in your login password and press enter.

---

