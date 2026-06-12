---
title: "Problem with stopping daemon process"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by n0kS on 2008-03-22
Hello, I installed yesterday MySQL v5 with the *apt-get install mysql-server* command. Later I removed it with *apt-get remove mysql-server* because I wanted to install xampp for linux (that includes mysql).... Here is the problem, I've just installed xampp and it says:
n0ks@n0ks-desktop:~$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.6.6...
XAMPP: Starting Apache with SSL (and PHP5)...
**XAMPP: Another MySQL daemon is already running.**
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

So I went to etc/ and removed the mysql folder .... (I think this was a bad idea) but I get the same error from xampp. Later I rebooted and I saw something like that: Starting MySQL daemon..... [[COLOR="Red"]fail[/COLOR]]

I tried *start-stop-daemon -nK mysql* (or mysql-server) but I get the same "No mysql found running; none killed."

How can I remove this from the daemon's list so I can start xampp's mysql without problems?

Thanks in advance :)

---

### Post by Athelstan101 on 2008-03-24
Hi,

You can stop the mysql server daemon manually by doing the following:
```
$ sudo /etc/init.d/mysql stop
```

To remove the daemon from startup (upstart) scripts, select 'System > Administration > Services' (there should be 3 'Database server' processes listed).

It's strange, however, that the mysql package doesn't seem to be completely removed after you uninstalled it. You could try the following to ensure that it's removed:
```
$ sudo apt-get --purge remove mysql-server
```

If it doesn't help, then try this followed by the '--purge remove' command (above):
```
$ sudo apt-get --reinstall install mysql-server
```

---

