---
title: "Searching for a very simple database application"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by stig on 2006-04-23
I have searched on Google for a simple software application (with GUI) to handle a small, simple database on Ubuntu but I am finding it difficult to undertand what might be suitable.

I have a database of customers for a subscription magazine which has their name and address details and their subscription period. I need to be able to do a query each month to select out those customers (and their addresses) whose subscription is paid up and will receive a mailing. Other simple queries such as listing all customers for a given country are necessary too. But my needs are very basic and simple.

OpenOffice Base looks very powerful but I would need only a tiny fraction of its power. I see there are applications such as Knoda, Kexia and Gnome-DB but (knowing little about database software) I am not clear whether these would do the job on their own or need other software. The term "front end" is often used and it sounds like I would need other software.

I hate using big software applications to do small, simple jobs and would love to find something appropriate.

There must be something out there which is at the level I need - any guidance would be gratefully received!

---

### Post by loell on 2006-04-23
openoffice calc might do the trick..

---

### Post by htinn on 2006-04-23
I haven't tried it, but Glom looks interesting.

[http://www.glom.org/wiki/index.php?title=Main_Page](http://www.glom.org/wiki/index.php?title=Main_Page)

---

### Post by garner_nc on 2006-04-23
I agree with using CALC. You can simply filter the data by the field you need. 

Though your needs may be small now, looking to the future your needs may grow leaving you needing more power. MySQL is as simple or complex as you want it to be. Also, you can connect to MySQL through Open Office Base to access your tables and enter data. The Open Office team has done a good job adding some M$ Access type functionality to Base. You might want to look at the combination.

All the Best,
Doug White
Garner, NC USA

---

### Post by stig on 2006-04-23
Thanks everyone for the suggestions and advice. I will have a look at using Calc - I know I can keep tables in it but I don't normally use spreadsheets and I'm not familiar with what they can do with filters (my waking hours are spent on editing and DTP!)

Would Gnumeric be able to do the same as Calc for database-type queries?

I've seen the Glom web site but there doesn't seem to be much mention of it elsewhere so I was a bit cautious!

---

### Post by stig on 2006-04-24
[QUOTE=htinn]I haven't tried it, but Glom looks interesting.

[http://www.glom.org/wiki/index.php?title=Main_Page](http://www.glom.org/wiki/index.php?title=Main_Page)[/QUOTE]

I see that on the Glom page it says:
"Glom uses the PostgreSQL database backend but it can not edit databases that it did not create, because it uses only a simple subset of Postgres functionality."

This sounds to me like I would not be able to import and use my current databases (from Paradox via cvs or dbf files)...unless I am misinterpreting the meaning of the sentence.

---

