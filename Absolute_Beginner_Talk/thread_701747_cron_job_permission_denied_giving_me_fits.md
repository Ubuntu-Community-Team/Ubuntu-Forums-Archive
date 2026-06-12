---
title: "cron job permission denied giving me fits"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Yamaboy on 2008-02-19
I'm nearly certain I've correctly added a cron job (tab) using the sudo cron command. The problem seems to be when the job actually runs. The entire directory in question is chmod'ed wide open. The resulting e-mail I receive when the job runs is;

```

From root@vivaubuntu.xxx.edu  Tue Feb 19 15:18:01 2008
Return-Path: <root@vivaubuntu.xxx.edu>
X-Original-To: root
Delivered-To: root@vivaubuntu.xxx.edu
Received: by vivaubuntu.xxx.edu (Postfix, from userid 0)
	id D2896104BBE; Tue, 19 Feb 2008 15:18:01 -0600 (CST)
From: root@vivaubuntu.xxx.edu (Cron Daemon)
To: root@vivaubuntu.xxx.edu
Subject: Cron <root@vivaubuntu> /opt/NSSDropbox/sbin/cleanup.php /opt/NSSDropbox/www/preferences.php > /opt/NSSDropbox/sbin/cleanup.log
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>
Message-Id: <20080219211801.D2896104BBE@vivaubuntu.xxx.edu>
Date: Tue, 19 Feb 2008 15:18:01 -0600 (CST)

/bin/sh: /opt/NSSDropbox/sbin/cleanup.php: Permission denied
```

I'm simply trying to run a cron job that someone has create an accompanying script for. Maybe it's the process itself that has trouble with the permission (I was changing those but I think they're all set back to default). 

I would think the php page should just run and do it's thing. The strange part is that the cleanup.php script creates a .log file in the directory just as it's supposed do. It just never seems to purge old files. Maybe because those files are in a different directory that have separate permissions?

Would that cause such an error?

I'll mess with it, but see if you can find any glaring errors.

Thanks.

---

### Post by Yamaboy on 2008-02-19
When I look at the directory, all the individual files created by the application own those files (www-data). Should running a cron job as root allow the php script to delete these as designed?

Is there a way to get around this if this is the issue?

---

### Post by dcstar on 2008-02-19
> **Yamaboy said:**
> When I look at the directory, all the individual files created by the application own those files (www-data). Should running a cron job as root allow the php script to delete these as designed?

Is there a way to get around this if this is the issue?

What are their permissions?

---

### Post by Yamaboy on 2008-02-19
The owner is www-data. All other permissions for group etc are 0 (rwx------). 

Is there a simple task I can create to see if cron is working otherwise? I'm trying to narrow down the possible causes.

Thanks.

---

### Post by Yamaboy on 2008-02-19
Well, I tried this;

sudo crontab -e
```
24 17 * * * /etc/init.d/apache2 restart
```

And the apache service restarted just fine.
```

From: root@vivaubuntu.xxx.edu (Cron Daemon)
To: root@vivaubuntu.xxx.edu
Subject: Cron <root@vivaubuntu> /etc/init.d/apache2 restart
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>
Message-Id: <20080219232413.13074104BBE@vivaubuntu.xxx.edu>
Date: Tue, 19 Feb 2008 17:24:01 -0600 (CST)

 * Restarting web server apache2
apache2: apr_sockaddr_info_get() failed for vivaubuntu
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: apr_sockaddr_info_get() failed for vivaubuntu
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
   ...done.
```

Has to be a problem with the script or the permissions I suppose. Still stumped though.

---

### Post by Yamaboy on 2008-02-19
For whatever reason this now works. I can't think of any changes I made other than recreating the cron job. Perhaps the only other difference was the php path that the page called.

#!/usr/bin/php5 needs to be the first line of the script. 

Sorry if I wasted any bandwidth. Hopefully my talking the problem out might help someone else.

Thanks.

---

