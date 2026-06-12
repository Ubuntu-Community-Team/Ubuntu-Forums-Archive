---
title: "i need to create a script to be executed hourly"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by dupa on 2007-02-06
I usually execute this command, to keep my system up to date.

sudo apt-get update
sudo apt-get upgrade

i want to keep continuosly my system update, it is a just a "console server".

i suppose i should create a script in /etc/cron.hourly
can you give me an idea about creating this cool script to keep always updated my whole system?
Thanks!

---

### Post by compmodder26 on 2007-02-06
Here you go

```
#!/bin/bash
apt-get update
apt-get upgrade
```

Save that in cron.hourly (use sudo) and set the permissions to 700.

Although, I must say that hourly seems a bit exessive.  Why not put it in daily?

Edit: for kernel upgrades, you'll also want to put "apt-get dist-upgrade" in there as well.

---

### Post by olejorgen on 2007-02-06
eh.. hourly? I doubt you need to update your system more than daily..

---

### Post by ComplexNumber on 2007-02-06
install an application called gnome-schedule. its in the repos. the version that i have seems as buggy as heck, though.

---

### Post by dupa on 2007-02-06
> **compmodder26 said:**
> Here you go

```
#!/bin/bash
apt-get update
apt-get upgrade
```

Save that in cron.hourly (use sudo) and set the permissions to 700.

Although, I must say that hourly seems a bit exessive.  Why not put it in daily?


thanks!! what do you think about:

```
#!/bin/bash
apt-get update -y -q > apt-get_update.log
apt-get upgrade -y -q > apt-get_update.log

```

Where do you suggest to put the log files?

Thanks!

---

### Post by dupa on 2007-02-06
> **ComplexNumber said:**
> install an application called gnome-schedule. its in the repos.

it's a server with just a console system.

---

### Post by compmodder26 on 2007-02-06
Yeah I forgot the -y part.  That is a must for auto-upgrading.  I would suggest putting the logs in /var/log, to keep with consistency.

---

### Post by dupa on 2007-02-06
> **olejorgen said:**
> eh.. hourly? I doubt you need to update your system more than daily..

i will have installed things such as apache.. so for eventual bug-fixes, i think that is important to check at least every hour to prevent hacker's attack.. no?

Thanks

---

### Post by compmodder26 on 2007-02-06
If you're wanting to keep logs then you'll probably want to look into logrotate.  Have a look at the  /etc/logrotate.d folder.  You can copy a script from there and adapt it to work with your new upgrade logs.

---

### Post by dupa on 2007-02-06
> **compmodder26 said:**
> Yeah I forgot the -y part.  That is a must for auto-upgrading.  I would suggest putting the logs in /var/log, to keep with consistency.

So the final script should be:

```

#!/bin/bash
apt-get update -y -q > /var/log/apt-get_update.log
apt-get upgrade -y -q > /var/log/apt-get_upgrade.log

```

Thanks a lot, i will try this one :)

---

### Post by compmodder26 on 2007-02-06
Just noticed you weren't appending the logs.  If that's your desire then don't worry about logrotate.  But if you want to append your logs (use >> instead of >), you'll  want to use logrotate to avoid a neverending log file that will eventually eat up all your hard drive space.

---

### Post by dupa on 2007-02-07
> **compmodder26 said:**
> Just noticed you weren't appending the logs.  If that's your desire then don't worry about logrotate.  But if you want to append your logs (use >> instead of >), you'll  want to use logrotate to avoid a neverending log file that will eventually eat up all your hard drive space.

thanks for the help! i will use >> instead of > and i will look for this logrotate stuff!

however i put that script:

```
$ sudo cat /etc/cron.hourly/auto-upgrade.sh
#!/bin/bash
apt-get update -y -q > /var/log/apt-get_update.log
apt-get upgrade -y -q > /var/log/apt-get_upgrade.log

```

But I cannot find any of these log in /var/log/

So i suppose that something goes wrong.. but i don't know to understand what's wrong.

the .sh have a 700 permission.
thanks.

---

### Post by dupa on 2007-02-07
> **dupa said:**
> thanks for the help! i will use >> instead of > and i will look for this logrotate stuff!

however i put that script:

```
$ sudo cat /etc/cron.hourly/auto-upgrade.sh
#!/bin/bash
apt-get update -y -q > /var/log/apt-get_update.log
apt-get upgrade -y -q > /var/log/apt-get_upgrade.log

```

But I cannot find any of these log in /var/log/

So i suppose that something goes wrong.. but i don't know to understand what's wrong.

the .sh have a 700 permission.
thanks.


i executed:


```
$ sudo /etc/cron.hourly/auto-upgrade.sh
```

it worked and the log files have been place in /var/log.

Cron seems to be in execution:

```
$ ps aux | grep cron
root      7911  0.0  0.1   2192   868 ?        Ss   10:10   0:00 /usr/sbin/cron
```

So i don't know why that script isn't executed automatically..

---

### Post by dupa on 2007-02-07
FYI, my /etc/crontab

```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#

```

---

### Post by ridgeland on 2007-03-02
Check this out:
[http://www.ubuntuforums.org/showthread.php?p=2238212#post2238212](http://www.ubuntuforums.org/showthread.php?p=2238212#post2238212)

I found that you cannot put a myscript.sh in /etc/cron.hourly
Delete the .sh and it will work.   name it just    myscript
or in your case change the name from
auto-upgrade.sh
to
auto-upgrade

Please post back the results.

---

