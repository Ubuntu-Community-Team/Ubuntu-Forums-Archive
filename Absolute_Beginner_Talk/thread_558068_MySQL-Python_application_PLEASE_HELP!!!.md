---
title: "MySQL-Python application PLEASE HELP!!!"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by CostaRica on 2007-09-23
Hi.  I have an accounting application I have been trying to develop for a while, but have had my difficulties.  

4 stores need to share a database, so that one knows what the inventory of the others are, etc.  Since the internet is kind of unstable in my country i would like to have the information synchronized to a central server back and forth, so that if the internet is down I would still be able to sell and make invoices. 

My dilemma is the following:
- Should I use my own central server in one of the stores or should I pay for a web hosting service?
- If I pay for a web hosting service, should the service be in my country for speed reasons?

It has been a LOT OF TIME spent learning to use ubuntu, MySQL and Python. 

I do not want to program in PHP, and I need badly a full example of an application with MySQLdb, wxPython forms and... reports!  What do you recommend?

Thanks in advance

---

### Post by LaRoza on 2007-09-24
> **CostaRica said:**
> Hi.  I have an accounting application I have been trying to develop for a while, but have had my difficulties.  

4 stores need to share a database, so that one knows what the inventory of the others are, etc.  Since the internet is kind of unstable in my country i would like to have the information synchronized to a central server back and forth, so that if the internet is down I would still be able to sell and make invoices. 

My dilemma is the following:
- Should I use my own central server in one of the stores or should I pay for a web hosting service?
- If I pay for a web hosting service, should the service be in my country for speed reasons?

It has been a LOT OF TIME spent learning to use ubuntu, MySQL and Python. 

I do not want to program in PHP, and I need badly a full example of an application with MySQLdb, wxPython forms and... reports!  What do you recommend?

Thanks in advance

0. Use what you can, I can't make business decisions for you, but do what is most economical and safe. 
1. Only you can answer that.

If you are developing this yourself, it would make sense to host it, if you have the means, and the time.

There are tutorials, and references on MySQLdb in my wiki, and references and tutorials for wxPython.

---

### Post by CostaRica on 2007-09-25
Thank you, LaRoza.

---

### Post by LaRoza on 2007-09-25
> **CostaRica said:**
> Thank you, LaRoza.

Hope it works out :D.

---

### Post by paulr on 2007-09-25
How about Rails ? Ruby is similar enough to Python so as to not have wasted your time. There is a python framework like Rails I think, but it isn't as advanced.

---

### Post by tvrg on 2007-09-25
1) why write it yourself?
2) why mysql?

i would strongly suggest looking at sql-ledger, it has accounting, inventory tracking, customer management etc allready built in. it's web based.
It doesn't run on mysql but it does on oracle and postgresql (both of which have better replication/syncing capabilities than mysql)

The drawback is that it's written in perl, but it is very stable and mature (we are using it at my company, very much to our satisfaction)

---

### Post by LaRoza on 2007-09-25
> **paulr said:**
> How about Rails ? Ruby is similar enough to Python so as to not have wasted your time. There is a python framework like Rails I think, but it isn't as advanced.

Don't push languages, unless the poster would benifit.

> It has been a LOT OF TIME spent learning to use ubuntu, MySQL and Python.

---

### Post by tvrg on 2007-09-25
> **paulr said:**
> Ruby is similar enough to Python so as to not have wasted your time. 
I've used both ruby and python, and i disagree. They are similar in a way that all programming languages are similar, but then again they are very different too (language is not all about syntax, but about libraries and modules etc.
> **paulr said:**
> There is a python framework like Rails I think, but it isn't as advanced.
I think you mean django, and i'm not sure why you are calling it less advanced.

---

### Post by LaRoza on 2007-09-25
> **tvrg said:**
> 
I think you mean django, and i'm not sure why you are calling it less advanced.

Maybe because the poster wasn't familiar enough with it to know the name or capability, but enough to compare it.

---

### Post by CostaRica on 2007-09-25
Yes, thanks for the advise, but I decided to not use web applications and center myself in Python.  I have been trying to develop this app for a LONG time (years) since I was trying to do it in M$.  It took me like three months to decide to use MySQL-Python-wxPython and at least for a while do not want to change again.

This app is for an optometrist's office franchise, so it is not such a standard business as to use a standard app for it.

I think I will host my own database server and keep reading!

Thanks a lot!

---

### Post by tvrg on 2007-09-25
maybe give dabo a look then:
[http://dabodev.com/](http://dabodev.com/)

---

### Post by CostaRica on 2007-09-25
davo crashed on my beloved ubuntu

---

### Post by paulr on 2007-09-29
> **tvrg said:**
> I've used both ruby and python, and i disagree. They are similar in a way that all programming languages are similar, but then again they are very different too (language is not all about syntax, but about libraries and modules etc.

I think you mean django, and i'm not sure why you are calling it less advanced.

That's it. By "advanced" I meant in development ; it isn't as mature as Rails I think. I got the impression Django was "Rails-in-Python".

I think the decision whether to host it locally or remotely is dependent on whether you need that facility. If you are using a MySQL DB then you can move it about anyway.

Have you decided whether your business logic is going to be on the server or on the client ? The advantage of having it server based is your client then becomes a "front end", and you could use a web front end if it ever became useful/needed.

People are moving towards MVC architectures these days.

---

