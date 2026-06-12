---
title: "Enable Root User Problems Server"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by drndrw on 2008-03-12
Hey guys. I just installed Ubuntu server on my server, and I am having trouble accessing the root user. I ran *$sudo passwd root*, but I got this error:

> sendmail: fatal: open /etc/postfix/main.cf: No such file or directory

How can I work around this? I need sudo to do just about everything. Thanks!

---

### Post by PinkFloyd102489 on 2008-03-12
Type "sudo -s" and then input your password when it prompts. Note that the password wont show up, but it's being entered. So type it in like normal and hit Enter. The user prompt will switch over to root@whatever.

---

### Post by drndrw on 2008-03-12
Yeah, I'm familiar with typing passwords in. Oh and why is that also? But I got this error:

> drndrw is not in the sudoers file.  This incident will be reported.
sendmail: fatal: open /etc/postfix/main.cf: No such file or directory

---

### Post by joshrobinson on 2008-03-12
> **drndrw said:**
> Yeah, I'm familiar with typing passwords in. Oh and why is that also? But I got this error:

```
sudo apt-get install -y postfix 
```

---

### Post by 0MG on 2008-03-13
If you aren't in the sudoers file, like he mentioned above, he isn't going to be able to sudo apt-get.

I am having the same problem right now.

---

### Post by joshrobinson on 2008-03-13
sorry i was half reading this thread or something

restart your computer, go into recovery mode, when you start up run
```
visudo
```

under user privilege specification, add the following..put your username where it says username

```
username   ALL=(ALL)  ALL
```

leme know if it works

---

### Post by drndrw on 2008-03-13
Hi. Well, here is my problem. My server is currently not connected to a monitor (but it I must, I can), and I am currently managing it via SSH. Is there any way to do this from SSH?

---

