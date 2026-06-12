---
title: "locked out-Incorrect username or password"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by MIPIO on 2008-02-23
After recently installing ubuntu 7.1 disk from  OSDisc.com in a PC
and starting ubuntu. I get (Incorrect username or password )
Q. If  I get my user name incorrect could I still proceed to my passward ?
Q2  how many chances do I get ,  or is there a time limit ?
I do not recall setting a username or passward when installing.
Q3 Can we go into a  safe mode ?
HELP!!!!
mipio

---

### Post by taurus on 2008-02-23
Dude, you asked the same question few hours ago and I already told you to boot into the recovery mode from GRUB menu and check to see what your login name is.

```
ls -la /home
```
And _assuming_ your login name is john, change the password to something that you can remember with

```
passwd john
```
Then, you can reboot and see if you can log in as john with that new password.

```
shutdown -r now
```
Otherwise, just post the output of this command here.

```
ls -la /home
```

---

### Post by MIPIO on 2008-03-16
taurus: I want to thank you for your help, I little late but I’m catching on.
mipio

---

