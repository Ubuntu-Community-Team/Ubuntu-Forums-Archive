---
title: "Can't get cron to work"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Toet on 2007-02-15
Hi,

I'm using ubuntu edgy, and tried to get a script to run hourly.

So I've put this script in the /etc/cron.hourly directory and made it executable. The path of the program in the script is in /etc/crontab.

Cron and anacron are running as far as I can see.

Can't find any logfile.

Can anyone tell me what I am doing wrong?

---

### Post by Yoooder on 2007-02-15
can you execute the script you've placed in /etc/cron.houry/ ?

If you can manually run the script, and it's successful then something is up with cron, otherwise something is wrong with your script

---

### Post by Toet on 2007-02-15
Yes I tested the script running it by itself, that works.

---

### Post by ehowell on 2007-02-15
Can you post up the crontab entry?

Also, make sure that you use absolute paths in the crontab entry, a lot of times problems I have are path related.

---

### Post by Toet on 2007-02-16
crontab:

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6	* * 7	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6	1 * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#

my script:

#!/bin/sh

#backup van de directories naar de usbdisk
/usr/bin/rdiff-backup /pictures /media/usbdisk/pictures.backup &
/usr/bin/rdiff-backup /music /media/usbdisk/music.backup &
/usr/bin/rdiff-backup /home/rex /media/usbdisk/rex.backup

#schoonmaken van de backup
/usr/bin/rdiff-backup --remove-older-than 10B /media/usbdisk/pictures.backup &
/usr/bin/rdiff-backup --remove-older-than 10B /media/usbdisk/music.backup &
/usr/bin/rdiff-backup --remove-older-than 10B /media/usbdisk/rex.backup &

---

### Post by Toet on 2007-02-17
Solved. The script in the /etc/cron.hourly directory is not allowed to have a "." in the name. It had.

---

### Post by ridgeland on 2007-03-02
Thank you!
I've been searching for the reason why my cron jobs are not running.
They had names like myscript.sh
I removed the .sh and now they work!!
This was not a problem in Fedora Core 6 
Thanks again for the answer.

---

### Post by nucklebone on 2007-03-09
i was just having the same problem with cron not running any of my scripts.

i looked for an error in my logs but couldnt find any. then i tried the mail command to see if cron reported any errors that way, but mail wasn't installed.

long story short. immediately after installing mailx and re-running the scripts via cron, my scripts work perfectly fine now. not sure why, but they do and installing mailx is the only thing i changed.

hope that helps.

nucklebone

---

### Post by simonn on 2007-03-22
I have had the same problem i.e. cron /etc/cron.{daily,weekly,monthly} were not running.

They would run if I did run-parts manually, so cron was the problem. 

When I installed xmail it worked. However, I do not want to have a mail server running (well actually I do not want to run anything I do not need).

I discovered that if you add:

```

MAILTO=""

```

To /etc/crontab, everything now appears to work. I guess this is because it does not fail if there is no mailserver because you have told it not to mail anyone.

---

### Post by ridgeland on 2007-03-23
Here's a thread that tells more about cron and anacron:
[http://www.ubuntuforums.org/showthread.php?t=375044](http://www.ubuntuforums.org/showthread.php?t=375044)
I solved my issues without any reference to mail so I don't know what it contributes.

---

