---
title: "rsync to backup to remote server"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by mfdc1969 on 2007-02-12
Greetings,

I am new to Linux/Ubuntu and experimenting with rsync to backup my machine to a remote server. My ultimate goal is to make a nice simple script that can be automated to backup nightly without my being present and generate a log on my desktop. I had success backing up /home after creating a RSA Key w/o passphrase which I then copied to the remote machine. Now I would like to add /etc directory and schedule a script. After reading MAN pages for rsync/crontab and scouring the forums I have arrived at a potential rsync command - I would love to have opinions/feedback on this:

# **rsync -e ssh -azvqpt -P -n --temp-dir=/tmp/bu_tmp/ --stats --include=/etc/ /home/michael michael@192.168.2.33:/home/backups/ubuntu-desktop >> /home/michael/Desktop/rsync_log**

(btw: what are the dangers of using the rsync option --delete)

So, if I add the above command to a file and name it /home/michael/backup.sh will this automate it to run in the early hours of the morning - say 1 AM?

- add my user name 'michael' to the file /etc/cron.allow 
- add a line to crontab using crontab -e that reads **0 1 * * * /home/michael/backup.sh**

ANY help/suggestions would be greatly appreciated!
Thank you.

Michael

---

### Post by bward1 on 2007-02-13
I'm not all that familiar with rsync so I can't answer that question.  Others before you have wanted the accomplish that same backup task, and so there are a few programs which you might try.  First there is a program called simplebackup and then there is another called backuppc.  You can do```
sudo apt-get install simplebackup
``` to install simplebackup and ```
sudo apt-get install backuppc
``` to install backuppc.  Both of these programs give you some more options as well that may have been a little more difficult to write in your script.  I hope this is helpful for you even though it doesn't directly answer your question.

---

### Post by mfdc1969 on 2007-02-14
Thanks for the suggestions ... I was hoping to aviod another program as rsync seems to do the job but, it's good to have suggestions such as this. I appreciate your taking time to reply and I will definatly look into these 2 progs - oddly enough a friend also recently recommended these same 2 progs.

As for my rsync command - it works from a terminal window but the script and cron attemp have failed - am I missing something in the way to use crontab? I added the rsync command to a file and named it /home/michael/backup.sh and made it executable then I added it to crontab:

- add my user name 'michael' to the file /etc/cron.allow
- add a line to crontab using crontab -e that reads 
0 1 * * * /home/michael/backup.sh

Hmmm ...

Thanks again for comments and help!

---

### Post by mn1957 on 2008-02-27
For help with running cron try this link, it sure helped me
[http://aplawrence.com/Unixart/cron.html]("http://aplawrence.com/Unixart/cron.html")

Its seems that environment variables cause the most cron failures.

---

### Post by kool_kat_os on 2008-02-27
> **mn1957 said:**
> For help with running cron try this link, it sure helped me
[http://aplawrence.com/Unixart/cron.html]("http://aplawrence.com/Unixart/cron.html")

Its seems that environment variables cause the most cron failures.

just to let you know.....cron runs in the background...so i think that you wont be able to see what its doing...i think


EDIT: is cron the same thing as crontab?

---

