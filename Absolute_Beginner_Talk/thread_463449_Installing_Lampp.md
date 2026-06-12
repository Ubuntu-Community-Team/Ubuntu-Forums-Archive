---
title: "Installing Lampp"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by PMatt on 2007-06-03
I downloaded Xampp for Linux and followed the steps from their site:

[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

I typed in the instructions from step two (was not logged in as root) and got this message. Help Please.

 @ -laptop:~$ tar xvfz xampp-linux-1.6.2.tar.gz -C /opt
lampp/
tar: lampp: Cannot mkdir: Permission denied
lampp/backup/
tar: lampp/backup: Cannot mkdir: No such file or directory
lampp/bin/
tar: lampp/bin: Cannot mkdir: No such file or directory
lampp/bin/CA
tar: lampp/bin/CA: Cannot create symlink to `CA.pl': No such file or directory
lampp/bin/captoinfo
tar: lampp/bin/captoinfo: Cannot create symlink to `tic': No such file or directory
lampp/bin/infotocap
tar: lampp/bin/infotocap: Cannot create symlink to `tic': No such file or directory
lampp/bin/ldapadd
tar: lampp/bin/ldapadd: Cannot create symlink to `ldapmodify': No such file or directory
lampp/bin/libpng-config
tar: lampp/bin/libpng-config: Cannot create symlink to `libpng12-config': No such file or directory
lampp/bin/php-5.2.1
tar: lampp/bin/php-5.2.1: Cannot open: No such file or directory
tar: Skipping to next header
tar: Error exit delayed from previous errors

---

### Post by noodle43 on 2007-06-03
> sudo tar xvfz xampp-linux-1.6.2.tar.gz -C /opt lampp/ just stick sudo infront of the code you were asked to type

---

### Post by bobplano on 2007-06-03
anytime you see "permission denied you need to use sudo. you are trying to put it in /opt it looks like and that is read-only for regular users

---

### Post by MenZa on 2007-06-03
Instead of using XAMPP, why not install Apache, MySQL, PHP, etc. seperately? There's great guide for it on the wiki:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by PMatt on 2007-06-03
> **noodle43 said:**
> just stick sudo infront of the code you were asked to type

I tried that and it didn't work, I missed the last lampp in the code. Thanks.

---

