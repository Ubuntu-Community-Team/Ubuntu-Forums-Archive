---
title: "Expect script and cron not working together"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by tmcmulli on 2007-12-14
I've read through so many posts my eyes hurt... I'm doing a cron job to back up files, and send them to my ftp server, which is unfortunately a Windows machine (hence using ftp).  The backup script works great.  But the Expect script will not run as a cron job.

From what I can tell, it looks like ftp just sends too much output to be run via cron.  Is anyone able to get this working??  I've run as a local user, root, you name it... at my last attempt and I feel there should be a way to do this!!

Any help is GREATLY appreciated!

Thanks!

---

### Post by tmcmulli on 2007-12-14
Used a .netrc file and cron works great:

[http://www.linux.com/feature/119510?theme=print](http://www.linux.com/feature/119510?theme=print)

---

### Post by tmcmulli on 2007-12-15
Interesting to note that on my 7.10 systems, the daily cron jobs run at 7:30 am, and are all run by the settings in /etc/cron.d/anacron

Some posts have said the cron.daily folder gets run at 1:30 am... but that isn't the case on a 7.10 desktop install.

---

