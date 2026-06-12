---
title: "Postgresql newbie steps in it"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by treaderll on 2007-01-29
I am running 2.6.17-10-generic Ubuntu 6.10. 
I know nothing about Postgresql, and decided to change that.
I used synaptic to install postgresql-8.1,version 8.1.4-7ubuntu0.1, and postgresql-server-dev-8.1, same version. 
Then I issued $sudo /etc/init.d/postgresql-8.1 start.  
Respose was  * Starting PostgreSQL 8.1 database server                               [ ok ]. 
Then I went to [http://www.postgresql.org/docs/8.0/static/tutorial-create](http://www.postgresql.org/docs/8.0/static/tutorial-create), where I read to $createdb mydb.  
Response was: createdb: could not connect to database postgres: FATAL:  role "mike" does not exist. 
I am clueless. 
From other posts here, I tried: $ su postgres 
Password: 
su: Authentication failure
clueless about password

What do I do to make createdb and createuser work? 
Thanks in advance, 
Treaderll

---

### Post by YoG%*@ on 2007-02-11
hell-o!

don't know if you're still looking for an answer, but maybe this helps: 
[https://help.ubuntu.com/community/PostgreSQL]("https://help.ubuntu.com/community/PostgreSQL")

greets
mux

---

