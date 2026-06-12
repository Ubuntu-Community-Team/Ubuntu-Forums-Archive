---
title: "Mysql Updation"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by anuraggautam on 2007-06-20
I want to update phpMyAdmin 2.10.2....i have oldest verion..please tell  me command so that i can update it...

and one more thing i want to IMPORT a data which is in .sql formate and of big size ....can you tell me commands or way so that  i can import it into my database..??

Please be fast !
Regards,
Thanks in Advance .:)

---

### Post by LaRoza on 2007-06-20
What is this data? You can input a file, and run the commands within with:

mysql -ularoza -p databaseName < file.sql

The contents of the sql file have to be valid, like the output from a mysqldump.

-edit The command is: mysql -u userName, you do not need a space in between, if you want to use your password type it after the -p with no space. If you want to output the query results, add a > fileName.txt at the end. This will redirect all output to a text file, you do not need to make one, it is made when you give the file name.

---

### Post by anuraggautam on 2007-06-20
i want to export a database which is 4 MB in size in my localhost......this file contains dictionary words....and some thing same about it...i have tht files in desktop.
 so tell me commands so that i can import that file [ which are in Desktop or any where in the system ] directly into my local database.

---

### Post by LaRoza on 2007-06-20
Can you copy the database? In mysql/data you should see your database, copy it to the data folder of your location. 

You could do a mysqldump on the database, which makes an SQL file and then use the above command to insert the database into the new server.

---

### Post by anuraggautam on 2007-06-20
Thxs its working  now......

thank you very much :)

---

### Post by LaRoza on 2007-06-20
Hold on, I am confused. You have MySQL, and it doesn't have the file in it. You have a file, in SQL, that you want to insert into a database? To do that:

```

mysql -u uName -p databaseName < locationOfFile

```

If this SQL file will create a database, omit the databaseName from the comment.

It would help if you posted the first SQL statements from this file so I can see what it is.

-edit I wrote this before you answered above.

---

### Post by anuraggautam on 2007-06-20
Do you have any idea about the clustering..i have to cluster the dictionary data ....can you help me in this

---

