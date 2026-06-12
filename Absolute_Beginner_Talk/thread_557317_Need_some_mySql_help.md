---
title: "Need some mySql help"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by adt41287 on 2007-09-22
Ok, what i am trying to do is take my sqlite database for Amarok and put it into mysql.  I have got a backup and everything from my sqlite database and when i go to import it through phpmyadmin it returns the error:  Column 'deviceid' cannot be null

i looked into my backup of sql lite and what it does it has an table with all your drives in it and gives it a number.  then when it stores each music file it associates it with the correct drive number.  what it looks like it did was set the 'deviceid' to NULL if amarok can no longer find the file in the path associated to the file and my question is, is there anyway to have that field except NULL??

in the sqlite file this query is ran to create the 'statistics' table where the error first occurs:
```
CREATE TABLE statistics (url VARCHAR(996),deviceid INTEGER,createdate INTEGER,accessdate INTEGER,percentage FLOAT,rating INTEGER DEFAULT 0,playcounter INTEGER,uniqueid VARCHAR(32) UNIQUE,deleted BOOL DEFAULT 0,PRIMARY KEY(url, deviceid) );

```

now in phpmyadmin, when i do an import this is the line it stops at (the null is in bold):
```
INSERT INTO statistics VALUES ( './Music/A.F.I/Decemberunderground/01 - AFI - Prelude 12_21 - Decemberunderground.mp3', **NULL** , 3257578203, 3257578203, 100.0, 10, 17, NULL , 0 );
```


like i said is there anyway around this without having to pick through every little bit of text and manually edit it? has almost 6,000 songs so it could take a while :mad:





(take it easy on my taste of music :) )

---

### Post by Jeroen Vernooij on 2007-09-22
Hi,
I found this article on digg today, did you also read it?
[http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html](http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html)

It looks like all you have to do is just install mysql, make a database, and change a setting in Amarok.

---

### Post by adt41287 on 2007-09-22
> **Jeroen Vernooij said:**
> Hi,
I found this article on digg today, did you also read it?
[http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html](http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html)

It looks like all you have to do is just install mysql, make a database, and change a setting in Amarok.

haha yes that is where i got the idea from.
theres a lot more to deal with it than just changing some settings.

---

### Post by Jeroen Vernooij on 2007-09-22
Ok
as far as I know (and I'm NO SQL or math expert) you are trying to make a field deviceid which only holds INTEGERS, and after that you insert a NULL in it. I thought INTEGERS cannot hold NULLS, so you should choose another field-type (VARCHAR maybe?)

However, this is no beginners question, people in [this forum]("http://ubuntuforums.org/forumdisplay.php?f=39") should be more knowledgeable about these matters.

---

### Post by adt41287 on 2007-09-22
thanks! ill try there

---

