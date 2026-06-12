---
title: "Clamav over network"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by AB34125 on 2008-01-20
I have clamav on my 7.10 install.

I would like to scan my windows PC over the network.

Is this possible? and if it is can people point to article on how to do it.

---

### Post by ikex on 2008-01-21
Samba\Cron job should do it, there could be more simple ways.
First, if you havent already you want to be able to access the files on the remote machine
[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/]("http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/")
after that you would want to schedule ClamAV to scan the files,
maybe something like this [stolen from google]:
```

#!/bin/sh


### fix log file if needed
LOG_FILE="/var/log/clamav/scan.log"
if [ ! -f "$LOG_FILE" ]; then
touch "$LOG_FILE"
chmod 644 "$LOG_FILE"
chown clamav.clamav "$LOG_FILE"
fi

/usr/bin/clamscan -r /LOCATION/OF/SHARE1 /LOCATION/OF/ANYMORE/SHARES \
--quiet \
--log="$LOG_FILE" \
--log-verbose \
--move=/var/log/infected \



```

then to schedule it, [https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto")

---

### Post by AB34125 on 2008-01-21
thank you, will have a look into this

---

### Post by AB34125 on 2008-01-22
Thanks for the help it did fix my problem.

---

