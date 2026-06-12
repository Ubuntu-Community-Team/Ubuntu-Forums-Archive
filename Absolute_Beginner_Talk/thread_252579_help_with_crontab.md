---
title: "help with crontab"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2006-09-07
```
13 6 * * * /var/backups/mysite/database/backup.sh
```


 
  it doesnt run... i cant find out why.... runing that exact same command manualy works without any problem... just dont get it.
  can anybody help me?
  i also try using @daily... but i don't know at what time does it update ( midnight i supose ) and i dont dare to wait a day.

---

### Post by mssever on 2006-09-07
> **pedrotuga said:**
> ```
13 6 * * * /var/backups/mysite/database/backup.sh
``` 
  it doesnt run... i cant find out why.... runing that exact same command manualy works without any problem... just dont get it.
  can anybody help me?
  i also try using @daily... but i don't know at what time does it update ( midnight i supose ) and i dont dare to wait a day.

Your job is scheduled to run at 6:13 am every day. The format looks correct to me.

Note, though, that you have to use the crontab command to edit your crontab. Do ```
crontab -e
``` if the command should run as your user and ```
sudo crontab -eu root
``` if it should run with root privileges.

If there are errors, you should get e-mail. if you have mutt installed, type mutt to check for mail.

---

### Post by pedrotuga on 2006-09-08
ok... 
the problem was in the output... the script was outputing files tothe default path, which aparently is not the on where the it is located.

I solved the problem adding

```
cd /var/backups/mysite/database/
```
 to the script.

btw... is there a way to get the script location path so i could use something like?

thanks msserver

```
cd $current_path
```

---

### Post by mssever on 2006-09-08
I'm not sure I understand your question. What script location path are you talking about? You aren't talking about $PATH, are you?

Perhaps you could post the relevant portion of the script.

---

