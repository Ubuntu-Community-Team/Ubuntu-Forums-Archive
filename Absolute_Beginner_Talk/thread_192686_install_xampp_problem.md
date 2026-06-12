---
title: "install xampp problem"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by verbatim210 on 2006-06-09
trying to get mysql apache and php server up and running.

1.downloaded xampp,

2.tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt

problem - results

jo@four:~$ sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt
Password:
tar: xampp-linux-1.5.3a.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
jo@four:~$ su
Password:
su: Authentication failure
Sorry.
jo@four:~$

---

### Post by adamkane on 2006-06-09
Looks like a typo or you need to make the file executable.

You should avoid XAMPP though - a PITA to troubleshoot.

---

### Post by fireshell on 2006-06-09
xampp is only a collection of available packages... Under  Adept search for mysql and install the server package (which ever version u want), search for apache and install 2.0, search for php and install which ever version you need. Here you will also need to install the php mysql connector.

That gives you php, mysql and apache. If you want webalizer or phpmyadmin both are also in the repositories

You may also want a graphical interface for mysql, the one I'm using is kmysqladmin... also available in the package manager.

When installing php, mysql and apache packages its probably better if you install more packages than you need straight away because you may find a feature u like to play with later on.

On my 256kbs broad band this took about 20 minutes to download and install, less problems than using the xampp installer and less configuration needed.

---

