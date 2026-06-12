---
title: "Postfix won't start"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Squizz on 2008-02-27
I'm trying to follow the tutorial [here]("http://www.howtoforge.com/perfect_server_ubuntu7.10_p5") on installing postfix because my old server died, but I'm failing miserably.

Here's what happens so far;

```

root@simon-desktop:~# apt-get install postfix libsasl2-2 sasl2-bin libsasl2-modules libdb3-util procmail
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsasl2-2 is already the newest version.
sasl2-bin is already the newest version.
libsasl2-modules is already the newest version.
libdb3-util is already the newest version.
procmail is already the newest version.
Suggested packages:
  postfix-mysql postfix-pgsql postfix-ldap postfix-pcre resolvconf postfix-cdb
The following NEW packages will be installed
  postfix
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1193kB of archives.
After unpacking 2904kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package postfix.
(Reading database ... 112792 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.4.7-1~gutsy1_amd64.deb) ...
Setting up postfix (2.4.7-1~gutsy1) ...
setting myorigin
setting relayhost: 
setting inet_interfaces: all

Postfix is now set up with the changes above.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Stopping Postfix Mail Transport Agent postfix                         [ OK ] 
 * Starting Postfix Mail Transport Agent postfix    

```

But then it just stops.   It's still trying to start postfix and won't do anything until I close the terminal.  If I try to reboot it does the same thing again, only it only boots into the command line.

Anyone know how to fix it?

---

### Post by kvizz on 2008-02-28
what kind of errors associated with postfix do you have in /var/log/messages?

---

### Post by dcstar on 2008-02-28
> **Squizz said:**
> I'm trying to follow the tutorial [here]("http://www.howtoforge.com/perfect_server_ubuntu7.10_p5") on installing postfix because my old server died, but I'm failing miserably.

Here's what happens so far;
........
Running newaliases
 * Stopping Postfix Mail Transport Agent postfix                         [ OK ] 
 * Starting Postfix Mail Transport Agent postfix    

But then it just stops.   It's still trying to start postfix and won't do anything until I close the terminal.  If I try to reboot it does the same thing again, only it only boots into the command line.

Anyone know how to fix it?

Post the contents of your /etc/hosts file.

---

### Post by Mr. C. on 2008-02-28
Postfix always logs its output: see and post the end of /var/log/maillog.

MrC

---

