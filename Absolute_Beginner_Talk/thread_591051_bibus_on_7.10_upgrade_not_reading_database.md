---
title: "bibus on 7.10 upgrade not reading database"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by jamaas on 2007-10-25
I've just upgraded to 7.1 from 7.04.  Tried using Bibus and it had some errors, found the fix for that but now it says all of my databases are encrypted or not a database.  Anyone else had this problem and found a solution?

thanks

Jim

---

### Post by pmartino on 2007-10-25
If bibus complains that it is an encrypted database it is because your database is in sqlite2 format and that you try to use it with a sqlite3 python driver (python-pysqlite2). This is the default driver for Ubuntu 7.10 and it would be difficult to go back to sqlite2 even if the python-sqlite is stil lin the Ubuntu universe repository.

I strongly suggest you to convert your database  to sqlite3.
Here is the procedure.
I will use old_db for the name of the file of your old db
and new_db for the new database that you will create

there are some scripts in /usr/share/bibus/db_models to help you

> apt-get install sqlite sqlite3
> sqlite old_db < /usr/share/bibus/db_models/savedata.sqlite > data.sql
> sqlite3 new_db < /usr/share/bibus/db_models/pysqlite2.sql
> sqlite3 new_db < data.sql

You should now be able to use your new database in bibus.
In addition, you have a human readable backup of your data in data.sql

Pierre
Bibus main developper

---

### Post by jackocleebrown on 2007-10-27
Hi Jim,

Please can I ask what you had to do to install Bibus on Gutsy? I am having some difficulty.

Thanks, Jack.

---

### Post by jackocleebrown on 2007-10-28
Got it installed now - from source.

---

