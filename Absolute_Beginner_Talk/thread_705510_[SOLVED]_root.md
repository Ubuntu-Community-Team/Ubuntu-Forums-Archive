---
title: "[SOLVED] root?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by marty1011 on 2008-02-23
Hi. I have started to use Ubuntu a week ago. I was wandering whether the root and the root password are the same as the user account or not. So far I am only using the account that I have created during the installation. I am using Gutsy Gibbon. I do not want to work as root at this point. If the root and the user account is the same what should I do?

---

### Post by mkoehler on 2008-02-23
In order to set the password for the 'root' account, use the following command.

```
sudo passwd
```

It will ask you for your new UNIX password, then again to confirm.

---

### Post by taurus on 2008-02-23
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by HermanAB on 2008-02-23
The Ubuntu install creates one user (you) with administration privileges. Read 'man sudo' and 'man sudoers' for details.

---

### Post by dje on 2008-02-23
You really shouldn't login as root, that's why it's disabled by default in ubuntu. Instead prepend 'sudo' to a command:
```
sudo *command*
```
or you can get a root terminal with
```
sudo su
```

dje

---

### Post by (((X))) on 2008-02-23
In short, NO
There is root account on your system, but it has no password, so by default ubuntu would´nt let you login as root, when you type sudo at the terminal, you basicly borrowing root priveleges. It isn´t same as logging in as root, ubuntu team isn´t stupid to let you do that.
sudo is even better than su if you ask me.

---

### Post by marty1011 on 2008-02-23
Thanks a lot for answering my question.

---

