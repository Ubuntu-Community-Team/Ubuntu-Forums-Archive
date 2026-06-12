---
title: "What do you use to backup your system?"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by nickburns on 2007-07-27
I see that there are several posts on ways to backup your system.  But what is the best ones and what do you use?

---

### Post by eentonig on 2007-07-27
I don't know which is 'the best one'

What works for me, is 'rsync'

Considering the fact that it takes about half an hour to install Ubuntu, there are only a few folders that I deem interesting for backup. Those are

Everyday Backup:
###########
/home/<username>/Images  (contains all my photo's)
/home/<username>/Music     (contains my music library)
/home/<username>/Docs       (contains.... well, 'docs')

Need to be backed up, but don't change that often:
###############################
/etc/
/var/www/
/var/log/

I created a script and scheduled that to run every night around 10pm. Since that is the time I'm mostly behind my desk.

The script starts and does the daily backups. Then it checks the logfile to see if it has already ran the full backup once this month. If not, it runs the remaining folders. At the end, it also saves a list of all installed packages and prepends 'sudo apt-get install' in front of that list.


I also have a script to does a manual full backup, that I'm supposed to use when I make some changes. But I tend to forget that. That's why I want to run that at least once a month.




This way, if I ever need to reinstall, I can easily reinstall everything I had before from that file and then restore all my configs to /etc.
When that's done, and for some reason my seperate partition with /home needs to be restored as well, I copy back my /media/backup/<username>/ folder with everything in it.

By that time, I usually reboot. I could restart all the required services by hand. But then again. With 30" shutdown and 40" to boot, it's just faster to reboot the thing.

---

### Post by ofir_k on 2007-07-30
> **eentonig said:**
> I don't know which is 'the best one'

What works for me, is 'rsync'

Considering the fact that it takes about half an hour to install Ubuntu, there are only a few folders that I deem interesting for backup. Those are

Everyday Backup:
###########
/home/<username>/Images  (contains all my photo's)
/home/<username>/Music     (contains my music library)
/home/<username>/Docs       (contains.... well, 'docs')

Need to be backed up, but don't change that often:
###############################
/etc/
/var/www/
/var/log/

I created a script and scheduled that to run every night around 10pm. Since that is the time I'm mostly behind my desk.

The script starts and does the daily backups. Then it checks the logfile to see if it has already ran the full backup once this month. If not, it runs the remaining folders. At the end, it also saves a list of all installed packages and prepends 'sudo apt-get install' in front of that list.


I also have a script to does a manual full backup, that I'm supposed to use when I make some changes. But I tend to forget that. That's why I want to run that at least once a month.




This way, if I ever need to reinstall, I can easily reinstall everything I had before from that file and then restore all my configs to /etc.
When that's done, and for some reason my seperate partition with /home needs to be restored as well, I copy back my /media/backup/<username>/ folder with everything in it.

By that time, I usually reboot. I could restart all the required services by hand. But then again. With 30" shutdown and 40" to boot, it's just faster to reboot the thing.

You can post here the script or post a link to it? I will really appreciate it! :) I am also looking for a script similar to the one you mentioned .

---

