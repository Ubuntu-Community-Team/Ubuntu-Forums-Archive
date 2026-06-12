---
title: "Using cron to autoupdate system."
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by pbaehr on 2006-08-28
I recently set up a cron job to run as root by using
```
sudo crontab -e
```

The job runs once a day and calls a script to write to a log and update the system. Here is the bash script:
```

#!/bin/bash
LOG=/var/log/updates
echo "***  Running updates on $(date)  ***">>$LOG
/usr/bin/apt-get -y update >> /var/log/updates 2>&1
/usr/bin/apt-get -y upgrade >> /var/log/updates 2>&1
echo "DONE"

```

That is a slightly modified version of an example I found on the internet.

The trouble is that when it runs it produces the following errors in the log if there are updates available:
```

dpkg: `ldconfig' not found on PATH.
dpkg: `start-stop-daemon' not found on PATH.
dpkg: `install-info' not found on PATH.
dpkg: `update-rc.d' not found on PATH.
dpkg: 4 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Am I correct in assuming that the job runs as root because I am using sudo when I edit the crontab file but because there is no actual root account on my system (and I don't want to enable one) there is no path for root and it can't find the programs that dpkg is relying on? I assume this is why apt-get is called with a full path in the script.

Any thoughts on resolving this without enabling a real root account? Is there a better way to go about it?

---

### Post by pbaehr on 2006-08-30
For the sake of anyone that comes across this post while trying to resolve the same problem, I've found the solution.

Apparently you can set a path in your crontab file. Adding the following to the top of my crontab
```
PATH=/usr/sbin:/usr/bin:/sbin:/bin
```
fixed the problem as the jobs running as root from cron are now able to find all the necessary programs to do their job.

---

