---
title: "How do I log-in as root in Ubuntu desktop?"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by hfnd on 2008-04-09
Hello,

gftpd tells me I need to be logged in as root but Ubuntu desktop won't let me log in as root.

Thanks,
John

---

### Post by bodhi.zazen on 2008-04-09
logging in as root is not supported on Ubuntu.

You run applications as root with sudo

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

for graphical applications use gksu (kdesu for KDE)

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

So ... in a terminal, 

```
sudo -i
```

start gftpd  from there

or add the command to /etc/rc.local if you want it active on boot.

---

### Post by Tatty on 2008-04-09
You cannot log in as root graphically.  You can log in as root via the CLI but that is not the reccomended way.

sorry im not aware of exactly what gftpd is as i have never used it, but to use it as "root" you need to do one of the following two things:

1.  If it is a non-graphical application, then you need to run it with ```
sudo gftpd
```
2.  If it is a graphical application then you need to run it with ```
gksu gftpd
```

This will explain why... [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by PeterJS on 2008-04-09
Ubuntu doesn't support using the root account, the support policy is covered here:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

Ubuntu instead uses sudo to access administrative functions:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tamoneya on 2008-04-09
you should not be logging in as root ever.  Instead what you should do is ```
sudo gftpd
```  Calling sudo will give you root privilages for just one command.  This is one of the reasons why windows is so much more susceptible to viruses.  The other main reason is that it presents a very large target to hackers and therefore has a larger payout if you can write a virus.

---

### Post by stchman on 2008-04-09
> **hfnd said:**
> Hello,

gftpd tells me I need to be logged in as root but Ubuntu desktop won't let me log in as root.

Thanks,
John

Logging in as root is possible but not recommended.  There are NEVER going to be situations where you will need to log in as root.  If a piece of software asks you to login as root don't use it.

There are plenty of ways to run apps as root with sudo or gksudo.

---

