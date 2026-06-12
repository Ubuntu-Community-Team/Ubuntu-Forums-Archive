---
title: "passwords"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by riso on 2008-04-03
as i'm the only person using the computer, is it possible to remove passwords, i.e. stop it asking for passwords?

thanks
riso

---

### Post by Tatty on 2008-04-03
if your computer is connected to the internet then that is a bad idea... anyone could access your computer.

---

### Post by kellemes on 2008-04-03
> **riso said:**
> as i'm the only person using the computer, is it possible to remove passwords, i.e. stop it asking for passwords?

thanks
riso

After reading this very carefully you'll never ask this question again.. ;-)
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by lswest on 2008-04-03
do you mean for sudo, or for logging in?  Because you can set the login window to automatically login to an account at boot, and you can add "NOPASSWORD" to the entry in the sudoers file (not sure of the correct syntax, someone else will know though :P).

---

### Post by kellemes on 2008-04-03
> **lswest said:**
> do you mean for sudo, or for logging in?  Because you can set the login window to automatically login to an account at boot, and you can add "NOPASSWORD" to the entry in the sudoers file (not sure of the correct syntax, someone else will know though :P).

This you do in the loginmanager (gdm) settings, "enable automatic login", or at least that's one way of doing it..

---

### Post by lswest on 2008-04-03
Yeah, i know how to do the automatic login, but i wasn't sure if he was asking about that, so i didn't post specific instructions, the syntax i'm not sure about is the NOPASSWORD line in the sudoers file so that "sudo" doesn't require a password.  In any case, i think he's after the no password for sudo.

---

