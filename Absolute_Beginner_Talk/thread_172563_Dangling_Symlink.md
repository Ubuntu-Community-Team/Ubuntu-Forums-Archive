---
title: "Dangling Symlink"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-05-08
How do I fix this?

I received in /var/mail/mark (my first name) the following:

mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink

The complete message is as follows:

From [email]root@localhost.loca[/email]ldomain  Sat May  6 09:19:09 2006
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: [email]mark@localhost.loca[/email]ldomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id ACC3A3D63E1; Sat,  6 May 2006 09:19:08 -0700 (PDT)
From: Anacron <root@localhost.localdomain>
To: [email]root@localhost.loca[/email]ldomain
Subject: Anacron job 'cron.daily' on lexington
Message-Id: <20060506161908.ACC3A3D63E1@localhost.localdomain>
Date: Sat,  6 May 2006 09:19:08 -0700 (PDT)
Status: O

/etc/cron.daily/bugzilla:
DBI connect('host=localhost;database=bugzilla;port=3306','bugzilla',...) failed: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) at /usr/lib/perl5/DBI.pm line 609
	DBI::__ANON__('undef', 'undef') called at /usr/lib/perl5/DBI.pm line 666
	DBI::connect('DBI', 'DBI:mysql:host=localhost;database=bugzilla;port=3306', '', '', 'HASH(0x871d278)') called at /usr/share/perl5/Bugzilla/DB.pm line 149
	Bugzilla::DB::_connect('DBI:mysql:host=localhost;database=bugzilla;port=3306') called at /usr/share/perl5/Bugzilla/DB.pm line 141
	Bugzilla::DB::connect_main() called at /usr/share/bugzilla/Bugzilla.pm line 142
	Bugzilla::dbh('Bugzilla') called at /usr/share/bugzilla/Bugzilla.pm line 157
	Bugzilla::dbwritesallowed('Bugzilla') called at /usr/share/bugzilla/globals.pl line 355
	main::GetVersionTable() called at /usr/share/bugzilla/lib/collectstats.pl line 56
 at /usr/share/perl5/Bugzilla/DB.pm line 149
run-parts: /etc/cron.daily/bugzilla exited with return code 2
/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink

---

### Post by Gannin on 2006-05-08
At the terminal, type &#8220;ls -l /usr/share/man/man1/rmic.1.gz&#8221; and see if it is indeed a symlink, if it points anywhere interesting, and if it's flashing red.  If it's flashing red, that means the file that it used to point to is now gone, and you can remove the symlink by typing &#8220;sudo rm /usr/share/man/man1/rmic.1.gz&#8221;.

---

### Post by Mark_in_Hollywood on 2006-05-08
The return is:

lrwxrwxrwx  1 root root 27 2006-04-14 15:48 /usr/share/man/man1/rmic.1.gz -> /etc/alternatives/rmic.1.gz

cursor flashes in color: black

---

