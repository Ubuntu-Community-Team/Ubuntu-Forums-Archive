---
title: "Schedule running a process and terminate after given length of time"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by jmknash on 2007-12-03
Hi
How would I go about using a schedule to run a process and terminate itself after given length of time, the process is airodump-ng. Jon

---

### Post by bwald on 2007-12-03
You could do this with a cronjob.  Cron is the system's way of running timed events.  [_Wikipedia article on cron_]("http://en.wikipedia.org/wiki/Cron").  The basic way it works is this, run the following command to edit your crontab:

```
crontab -e
```

This will edit your user's crontab.  The file might be blank if you've never used it before.  The timing can be a bit complicated, but a crontab is structured with 6 columns.

From the Wikipedia page:

```

# +---------------- minute (0 - 59)
# |  +------------- hour (0 - 23)
# |  |  +---------- day of month (1 - 31)
# |  |  |  +------- month (1 - 12)
# |  |  |  |  +---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
  *  *  *  *  *  command to be executed

```

So if you wanted to run airodump-ng, say every day at 8:00, you'd do the following:

```
* 20 * * * airodump-ng
```

This means "every minute, only on the 23rd hour, every day of the month, every month, every day of the week"

To stop airodump after a few hours, you could do:

```
* 23 * * * killall airodump-ng
```

This will kill all processes called "airodump-ng."

More information:
[_https://help.ubuntu.com/community/CronHowto_]("https://help.ubuntu.com/community/CronHowto")

---

### Post by jmknash on 2007-12-03
Nice,  thanks for the detailed reply bwald.

---

### Post by jmknash on 2007-12-03
Is there a way to issue it as a command manually and not daemon and stop it self, because as the program is running I will loose
remote connection to the machine.

example script:

airodump-ng
wait 10 minutes
killall airodump-ng

---

### Post by jmknash on 2007-12-03
Would setting up a background cron job to run 'killall airodump-ng' every 30 mins work,
So i could run airodump-ng at any half hour and wouldn't run past that time window?

Jon

---

### Post by bwald on 2007-12-03
Yeah, that makes sense.  But remember, Cron sends out commands at timed intervals, it doesn't know when you start your command manually.  If you wanted to, you could set cron to "killall airodump" to go off at the n:30, where n is every hour of the day.  If you started airodump at, say 2:25 then it would be killed at 2:30, even if it hadn't run for 30 minutes.

---

### Post by jmknash on 2007-12-04
ouch, I thought it worked like that. I was looking around in webmin on my server and found custom commands which you can run script etc and it has a timeout which says will kill a program after a specific time, but It didn't say what the command is what would be used in help?..

---

### Post by jmknash on 2007-12-04
Can't get a cron task to work in background..below is the command..

 dbclient -R 10001:localhost:22 tunnel@192.168.10.10 -i /jffs/ssh/dropdss -y

(I tried -y to force it to ignore host key otherwise without -y it says ..
Host '192.168.10.10' is not in the trusted hosts file! bugger.)

-----------
This all runs if I connect to my box via ssh or telnet and run it manually!
But automatically using cron it doesn't appear in top, there is no connection to 
my server either.

Tested run as command in server http web admin, output is:

dbclient: Warning: failed creating //.ssh: Read-only file system
Host '192.168.10.10' key accepted unconditionally.
(fingerprint md5 6a:9f:****:***)
dbclient: Failed reading termmodes


?????wtf


please help, thx jon
# (*just covering my identity....)

---

### Post by jmknash on 2007-12-05
Solved. Got it to run as background process without a TTY
dbclient -f -N -R 10001:localhost:22 tunnel@192.168.10.10 -i /jffs/ssh/dropdss -y

---

