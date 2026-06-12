---
title: "database questions"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by dysolve on 2007-03-19
Hello all.

I am not sure where to post this but since I am a beginner I suppose this will work. My wife built her self a small database using Open Office. She built her self Tables, Forms, Query's and reports. Now I need to know How to run the database externally to open office and on my ubuntu server. But theres where my knowledge ends. I may use database's all day a work but I have never had to set one up as such. The database is just saved as a openoffice file, what do I have to do to run it in ubuntu? If I have asked this question in the worng place just let me know were the right place is and I will go there

Thanks in advanced
David.

---

### Post by justleen on 2007-03-19
If i understand corretly, you created a DB in Open Office, and now you want to run it stand alone?

---

### Post by Jussi Kukkonen on 2007-03-19
Well, it sounds like she's using the database engine included in OO.org. It's not possible to run that as a service as far as I can tell.

You'll just have to build it up again on another (real) database. Depending on the stuff she's done, this may be quite easy or quite a lot of work... OO.org Base does support a lot of DBs natively, and the rest through ODBC, so moving the actual data should be pretty easy one you have the tables and such created.

Select a DB and start reading docs and asking questions, that's my advice.

---

### Post by dysolve on 2007-03-19
Now I am very confused. So open office is not the right software to use if I want to make a standalone database? If that is the case then want would be my best option for ubuntu? I have completely missed the point of this LOL..

---

### Post by justleen on 2007-03-19
> **dysolve said:**
> Now I am very confused. So open office is not the right software to use if I want to make a standalone database? If that is the case then want would be my best option for ubuntu? I have completely missed the point of this LOL..

No, you cannot create a " stand alone" database with Open Office. You will laways need OO to open it. 

What you can do, is export your DB to a diffeerent format, for example to cvs, and import it in, for example in mysql. 
Mysql runs as a deamon (service/server ) in the background which alows you to access the database without the need of opening Open Office.

As the poster above suggested, Open Office supports a large amount of different datases. So if this is really what you want (that is, have the DB always running without OO) you should investigate these possibilties.

---

