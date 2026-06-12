---
title: "How do you log on as root?"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by shishio on 2006-02-25
What are the commands in terminal to login as root?

---

### Post by aysiu on 2006-02-25
[QUOTE=shishio]What are the commands in terminal to login as root?[/QUOTE] You don't log in as root

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/linux/permissions.php](http://www.psychocats.net/linux/permissions.php)

---

### Post by taurus on 2006-02-25
Is there any reason you want to log in as root?  If you need to do something as root, use sudo instead.

```

sudo <command>

```

---

### Post by gila_monster on 2006-02-25
Generally, you won't want to. Anything you might need to do as root you can do using the sudo command. This is to help prevent box-killing accidents.

If you really need to be logged in as root, you can use

  sudo su

and enter your main account password at the prompt.

gila

---

### Post by shishio on 2006-02-25
Wow. That was quick. Thanks for the help.

---

### Post by taurus on 2006-02-25
If you want some real quick replies, just say that you are a newbie and you want to log in as root so you can explore your system!!!  Then, replies will come fast and thick...  :twisted:

---

