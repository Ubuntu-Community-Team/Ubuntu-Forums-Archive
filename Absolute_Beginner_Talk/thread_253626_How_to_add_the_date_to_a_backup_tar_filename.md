---
title: "How to add the date to a backup tar filename"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by jordi_rc on 2006-09-08
Hello!

I am learning to do my backups with cron.
Maybe this be correct?:

0 12 * * * tar -cfz /home/backup/backup.tar.gz /opt/lampp/htdocs/myweb/*

I want to make a backup all week days of every month at 12:00 PM saved in /home/backup/ of all the contents of myweb at /opt/lampp/htdocs/myweb/. 

As for the moment I have my server shut down, I will use acron with this command:

acrontab -e

Now the most important:

I want save all my backups so if one of them is corrupt, I can restore the preceding.
So I have the idea to add the date and hour to the tar.gz filename.

So I have for example: backup_12:00_10_september.tar.gz, backup_12:00_11_september.tar.gz... etc.

How can I do this?

I also want to make a backup of mysql table. What is the command in Xubuntu to make a backup of a mysql table??

That's all!

Thanks  for your help!

Jordi

---

### Post by duff on 2006-09-08
Does cron allow for shell expansion?  I do something similar in my Makefiles using the "date" command.

```
$(date +"%Y-%m-%e"|sed -e "s/\ /0/g")
```
gives the date in YYYY-MM-DD format.  You could fiddle around with date's parameters if you want "september" instead of "09", but I wanted mine to show up in order.

---

### Post by bswilson on 2006-09-08
How about modifying your cron script to automatically append the date?

```
0 12 * * * tar -cfz /home/backup/backup_`date +%Y-%m-%d`.tar.gz /opt/lampp/htdocs/myweb/*
```

This will give you files such as:

```
/home/backup/backup_2006-09-08.tar.gz
/home/backup/backup_2006-09-09.tar.gz
/home/backup/backup_2006-09-10.tar.gz
```

etc...

---

### Post by whizbaby on 2006-09-08
You could write a little script using the **date** command (**man date**). With the format options at the bottom of the manual you can control the output pretty well. Store your desired output in a string and concatenate it with the rest of your whished filename to the final name of the archive. Then **tar *final name***.
EDIT: I see I come too late...

---

### Post by jordi_rc on 2006-09-10
Hello.

Thanks for all your suggestions, that helped me to find the solution.
I made a syntax error: tar arguments don't have a - sign.

The solution was to create a shell script:
-----------

#!/bin/bash


#################################
#  $b is the date with hour     #
#################################

b=$(date +%d_%m_%Y_hour_%H_%M)

###########################################
# Backup all the files and       database #
###########################################

mkdir /backup/$b/

# Archiving using tar, all permissions kept in tact

tar pczf "/backup/$b/backup_web.tar.gz" "/opt/lampp/htdocs/web"
/opt/lampp/bin/mysqldump -u root xoops > /home/backup/$b/database_xoops.sql


----------------


Then copy it to /etc/cron.daily.

I suppose this will execute each day. Is this right?

If I turn my PC off, the backup will be performed when I turn it on? Or not? How can I get that done?

Thanks.

Jordi

---

