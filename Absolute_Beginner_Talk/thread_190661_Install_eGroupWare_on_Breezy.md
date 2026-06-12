---
title: "Install eGroupWare on Breezy???"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by OMRebel on 2006-06-06
I apologize if this is in the wrong forum, but I'm trying to install egroupware on a Breezy install, but cannot get the database created.  I've searched the web, and can't find the answer.  If anyone here has any experience with installing this and can help, I'd certainly appreciate it.
---------------------------------------------------------
Database error: ADOdb::Connect(dbname=template1 host=10.4.*.*** port=5432 user=postgres password='*****', , $Password, ) failed.
pgsql Error: -24 (-24)

Function: db::query / db::create_database

Database error: ADOdb::Connect(dbname=egroupware host=10.4.*.**** port=5432 user=postgres password='*****', , $Password, ) failed.
pgsql Error: -24 (-24)

Function: db::create_database
egroupware
-----------------------------------------------------------

This is using postgresql.  I have mysql installed, but egroupware isn't recognizing it for some reason.

---

### Post by lreyes6 on 2006-06-06
mjm... did you read the readme? 

can you explain more your problem? maybe [this]("http://www.egroupware.org/specialpages/?page_name=knowledgebase&menuaction=phpbrain.uikb.view_article&art_id=26") helps you...

---

### Post by denisesballs on 2006-06-07
I have the same problems on dapper, it complains when filling the databases and then those errors are reflected later.

---

### Post by adamkane on 2006-06-07
Unfortunately there aren't many postgresql users on the ubuntu forums. Postgresql is great, but it is also a PITA to install and configure.

I can help you get mysql up and running, if you are so inclined.

---

### Post by denisesballs on 2006-06-07
I was poking around the eGroupware forums and I found that if you download the latest version, everything is copacetic. I've had it running for a few hours now, very nice.

---

