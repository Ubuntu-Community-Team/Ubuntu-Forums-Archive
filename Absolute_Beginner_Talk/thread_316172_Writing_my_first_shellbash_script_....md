---
title: "Writing my first shell/bash script ..."
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-12-10
Hello,

I am new to Linux; wanted to write my own little script (bash/shell -- not sure what to call it) ... basically, I want to be able to backup a number of my mysql databases by making a call to a script instead of typing out the mysqldump commands for each database every time.  (When I learn a little more, would like to make a cron job out of it.)

I searched a little online but couldn't find any of the shell/bash scripting basics I need; I just want to create one variable for today's date ($date), one array of database names ($dbs) and then a loop to go through that array, calling to following command each time:

```

mysqldump --add-drop-tables -u root -p mypassword $dbs > $dbs-$date.sql 
```

Can you help ?  

Thanks! (Linux is sexy and exciting.)

---

### Post by steve.horsley on 2006-12-10
It's not s bash script, but this pyton script should do it for you:


```
#!/usr/bin/python
import time, os
dblist = ["db1", "db2", "db3"]
date = time.strftime("%Y-%m-%d")
for db in dblist:
    os.system("mysqldump --add-drop-tables -u root -p mypassword %s > %s-%s.sql" % (db, db, date))

```

---

### Post by speedman on 2006-12-10
mkdir /home/backups

sudo gedit /usr/local/bin/sql-dump

insert this:

===== copy below here

#!/bin/bash

cd /home/backups

for i in $(ls -F /var/lib/mysql/|grep \/|cut -f1 -d/) ;
        do mysqldump -u root -pPASSWORD $i > $i.`date -I`.sql ;
done

===== copy above here

replace PASSWORD with your password and save the file.

make the script executable:

chmod +x /usr/local/bin/sql-dump

sudo gedit /etc/crontab

add this to the end of the file:

0 0     * * *   root    /usr/local/bin/sql-dump >/dev/null

save the file.

if you want to do run a manual backup just run the command sql-dump.  otherwise the crontab entry will do it for you every day at midnight.

hope that helps.


sm

---

### Post by thornomad on 2006-12-10
Hello there!!  Thank you both!! That python script is very simple, however, the bash script is awesome!!  I love it!!  I was trying to figure out a simple way to do the:

```
for i in $(ls -F /var/lib/mysql/|grep \/|cut -f1 -d/) ;
do mysqldump -u root -pPASSWORD $i > $i.`date -I`.sql ;
done
``` 

Amazing.  

Thanks again, I had been playing around with getting the output into a temporary directory and then bzip2-ing the whole thing; but I can throw away the junk for-loop I had written and use this one instead with the zipping option.

Thanks.  

Linux is amazing.

---

