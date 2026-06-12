---
title: "Mediawiki1.9 cannot make new users"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by wantime on 2007-02-26
I recently reinstalled my whole system and during the process backed up my wiki (mediawiki1.7).  On the new system I installed mediawiki1.9 and restored the database, almost no problems.  My problem is that now I can only log in as the administrator and cannot make any new users.

I get the following error:
<pre>
Database error
A database query syntax error has occurred. This may indicate a bug in the software. The last attempted database query was:

    (SQL query hidden)

from within function "User::addToDatabase". MySQL returned error "1054: Unknown column 'user_newpass_time' in 'field list' (localhost)".
</pre>

One thing that I believe may have caused some problem is that I changed the prefix names of the files in the database from none to something.  When I couldn't load the database, I went into LocalSettings.php and changed the prefixes back again and deleted all the databse files that were created from the new name.

It all loads ok,I can create new pages etc.  I just can't create users or log in as pre-existing ones.

Has anyone got any ideas to help me out?  Thanks.

---

### Post by wantime on 2007-02-27
OK .... After some thought ...

I logged into mysql as root and then ran the following command:

mysql> alter table user add column user_newpass_time varchar(20);

This allowed logins for old users that were created before the reinstall but I then had an error when I tried to create a new user which asked for a column  user_editcount in the "field list" which I could not see in the wikidb tables list.  Seeing as the problem was also "User::addToDatabase"  I ran the following mysql command:

 alter table user add column user_editcount varchar(20);

Ie, creating the column in the user table.  This seemed to work ok.  

Overall I guess this is more to do with mysql than ubuntu, I just find it strange that this error occurred at all during the reinstall of mediawiki.

Problem solved for now.

---

