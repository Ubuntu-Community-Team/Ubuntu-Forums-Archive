---
title: "Strange cron problem running .sh script"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by wormie_dk on 2007-08-23
Hi there.

I am trying to get cron to run a backup script I have created which is called backup.sh

My crontab looks as follows:
```
# m h  dom mon dow   command
52 12 * * * rsync -e ssh -avz --delete-after [email]abc@abc.dk[/email]:/home/mail /data/Bak 2>&1 > /home/user/rsync_mail
52 12 * * * rsync -e ssh -avz --delete-after [email]abc@abc.dk[/email]:/home/public_html /data/Bak 2>&1 > /home/user/rsync_public_html
52 12 * * * /home/user/backup.sh
```

The two first rsync commands run great however the shell command is not run. I tried testing my backup script using [http://ubuntuforums.org/showthread.php?t=518675&highlight=cron+shell+script](http://ubuntuforums.org/showthread.php?t=518675&highlight=cron+shell+script) and it runs fine in the cron environment. 

Furthermore I created a very basic b.sh file containing:
```
#!/bin/sh
touch /home/user/i_ran
```
which I chmodded 755 and tried this crontab
```
52 12 * * * /home/user/b.sh
```
However it doesnt run either. 

Then I tried copying b.sh to /usr/bin and tried this crontab
```
52 12 * * * b.sh
```

But none of them seem to run...

Finally I tried
```
52 12 * * * touch /home/user/i_ran which did not seem to work either.
```

Now I am confused... rsync runs fine but none of the other commands will work :-(

---

### Post by Dr Small on 2007-08-23
To run the shell command, from crontab, add "sh" before the path to the script ;)

---

### Post by wormie_dk on 2007-08-23
> **Dr Small said:**
> To run the shell command, from crontab, add "sh" before the path to the script ;)

Tried
* * * * * sh /usr/bin/b.sh

It still doesnt run

---

