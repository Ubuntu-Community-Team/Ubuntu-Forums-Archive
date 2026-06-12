---
title: "How do I log into ubuntu if i forget username and pass?"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by baysl on 2007-02-12
I forgot my username and password and now I 
cant login to ubuntu?

Is there a solution for this problem?

---

### Post by taurus on 2007-02-12
Boot into recovery mode from the GRUB menu.  At the prompt, see what's your username is and change the password for that username.  

```
ls -la /home
```
You should see your login name (directory) from the output of that command.  Assuming it's **baysl**, change the password for **baysl** with

```
passwd **baysl**
```
Reboot and see if you can log in now.

```
shutdown -r now
```

---

### Post by hub_cap on 2007-02-12
I got to the recover mode with this prompt
root@ubuntu:~#
when I typed "ls -la/home", I received the following:
ls is an invalid option -- /
Try 'ls --help' for more information

What am I doing incorrectly? Thanks:(

---

### Post by compmodder26 on 2007-02-12
place a space between -la and /home

---

### Post by hub_cap on 2007-02-12
Never mind, I left out the space between '-la /home'. I'm there now.

---

