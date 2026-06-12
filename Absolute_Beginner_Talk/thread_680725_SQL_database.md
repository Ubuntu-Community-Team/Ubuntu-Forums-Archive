---
title: "SQL database"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by bardic on 2008-01-28
Is there an IDE I can use to connect to a MS SQL database. I have read other posts but they have been vague without providing an actual answer...

If the MySQL tools can do it, that'd be great, but if not, is there any other way?

---

### Post by Paul41 on 2008-01-28
There is a MySQL admin tool ([http://packages.ubuntu.com/gutsy/admin/mysql-admin](http://packages.ubuntu.com/gutsy/admin/mysql-admin)) and a query tool ([http://packages.ubuntu.com/gutsy/misc/mysql-query-browser](http://packages.ubuntu.com/gutsy/misc/mysql-query-browser)).  You can also use phpmyadmin([http://packages.ubuntu.com/gutsy/web/phpmyadmin](http://packages.ubuntu.com/gutsy/web/phpmyadmin)).

---

### Post by emarkd on 2008-01-28
Paul41:  Not for MSSQL

bardic:  Have you tried [http://www.aquafold.com](http://www.aquafold.com)  I've never used it so I can't recommend it, but it's java so it should run fine.

---

### Post by Paul41 on 2008-01-28
> **emarkd said:**
> Paul41:  Not for MSSQL

bardic:  Have you tried [http://www.aquafold.com](http://www.aquafold.com)  I've never used it so I can't recommend it, but it's java so it should run fine.

Your right...sorry I thought it said MySQL

---

### Post by emarkd on 2008-01-28
I had a whole answer about phpmyadmin typed up before I realized what it actually said.  We're not used to seeing MS-SQL around these parts :)

---

### Post by angelot on 2008-01-28
Can emarkd please define $clever_quote :-)

---

### Post by emarkd on 2008-01-28
I could try, but then again I'd probably just do a google search and cut-n-paste :)  Does that count?

Hey, we all have our strengths as well as our weaknesses, right

---

### Post by bardic on 2008-01-28
So I have installed squirrel sql, but I have no idea now how to get it to connect to a sql database...

Anyone have any experience with Squirrel SQL?

---

### Post by apostate on 2008-01-29
Well,

I don't know Squirrel, but if it is a generic DB query explorer type thing, you will need to give it a connection string.  DB URLs are different than webpage URLs, and I am not certain of the MS SQL syntax, but it would look something like:
 "Driver={SQLServer};Server=Your_Server_Name;Database=Your_Database_Name;Uid=Your_Username;Pwd=Your_Password;"

---

