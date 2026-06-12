---
title: "Conversation with su failed"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by xlib on 2006-04-01
Everytime I try to log in as root so I can do things on my computer the error "Conversation with su failed" comes up. It let me in once, I was trying to change the time because I just installed Kubuntu. So it let me log in once, then it isn't letting me back onto root.

What do I do to fix this?

---

### Post by taurus on 2006-04-01
You don't have to log into root because you can't!!!  If you want to make some changes to system's files, try using sudo instead...
```

sudo gedit filename
(then enter the same password that you use to log into your account...)

```

---

### Post by gord on 2006-04-01
sudo is ubuntus security consious replacement for root, in many ways its better than root, you can find otu all the info [here](https://wiki.ubuntu.com/RootSudo)
you can still enable the root account if you must, but its not recomended, you can do all the things you used to be able to do with a root account with sudo.

---

### Post by catlett on 2006-04-01
If you are following examples from other Linux distros and it says log in as root. That doesn't pertain to Ubuntu. In some other distros you have to log off. Log in by typing root and its password. Do your commands and then log out, log in as user. Ubuntu simplifies that. When you need root privileges in Ubuntu you get them temporarily with sudo. There is no need to log off log on. By typing sudo you are invoking root privileges. When you need to be root, type sudo whatever /whatever. There will be a password prompt. At this prompt you enter your user password. You won't know the root password because Ubuntu won't give it to you. When you go through install you make a user name and user password. Ubuntu makes a root password and stores it without telling you what it is. Ubuntu then sets up "superuser" accounts. Your username from install will be automatically be entered into the superuser file. When you type sudo (which is made from "superuser do") you are invoking your superuser status. The computer then wants your password to make sure it is you the user with superuser privileges. To sum up. You will never (under normal circumstances) log in as root. You will always type sudo before your command to get root privileges. Regards.

---

