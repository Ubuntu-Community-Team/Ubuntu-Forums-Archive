---
title: "How to backup mysql database with shell script"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by jordi_rc on 2007-03-17
Hello

I had a shell script to backup my website and Mysql databases. Now, as I changed the password for root, these lines stopped to work:

> 
b=$(date +%d_%m_%Y_hora_%H_%M)
mkdir /home/backup/$b/

/opt/lampp/bin/mysqldump -u myuser  myDB > /home/backup/$b/myDB.sql



And if I add this:

/opt/lampp/bin/mysqldump -u myuser  -p mypassword myDB > /home/backup/$b/myDB.sql

It doesn't works too.

How can I specify the password or get this working again?

Thanks friends.

Jordi

---

### Post by jordi_rc on 2007-03-17
I solved. I had:

/opt/lampp/bin/mysqldump -u myuser -p mypassword myDB > /home/backup/$b/myDB.sql

And it was:

/opt/lampp/bin/mysqldump -u myuser -pmypassword myDB > /home/backup/$b/myDB.sql

without the space between -p and password. A stupid error.

Jordi

---

