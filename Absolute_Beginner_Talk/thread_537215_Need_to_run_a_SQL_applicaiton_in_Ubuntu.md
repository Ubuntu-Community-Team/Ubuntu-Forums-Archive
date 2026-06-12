---
title: "Need to run a SQL applicaiton in Ubuntu"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by jkarns on 2007-08-28
I am looking to impress the boss and save a ton of money by converting to Ubuntu. We are about to purchase around 40 new fit-PC mini computers that come preloaded with Gentoo. I am Ubuntu fan, so I would like to load it. BUT, if I can't get this one application to work...we will have to by licences for Windows XP. I am not diggin that idea at all, there has got to be a way to make this work. 

We have developed an in house program for our company's day to day operations. It is a SQL Application, and I cannot seem to get it to work in WINE or Crossover. I am able to install it, but it will not connect to the database that runs it which is on a Windows domain. I get this error:

Run-time error '429':
ActiveX component can't create object. 


Any ideas? Most of these new computer will run ONLY this application, so it is very important that it works.

---

### Post by deadgobby on 2007-08-28
Install MySQL  in synaptic  or DL from [http://www.mysql.com/](http://www.mysql.com/)
 Gentoo is a good system and there are fans of that O/S, I am sure you are going to make some one cringe.

Gobby

---

### Post by jkarns on 2007-08-29
SO, should installing MySQL allow me to connect to a SQL server on a Windows machine on Ubuntu? 

Anyone else have any ideas on how to make this work?? Only got one reply, hoping for alot of help here. Thanks!

---

### Post by LaRoza on 2007-08-29
> **jkarns said:**
> SO, should installing MySQL allow me to connect to a SQL server on a Windows machine on Ubuntu? 

Anyone else have any ideas on how to make this work?? Only got one reply, hoping for alot of help here. Thanks!

You did not mention SQL Server, MySQL is a RDMS Server, probably a better choice for using on Linux.

---

### Post by jkarns on 2007-08-29
Again, what I am trying to do is connect to a SQL driven Visual Basic application on a Windows Domain

---

### Post by LaRoza on 2007-08-29
> **jkarns said:**
> Again, what I am trying to do is connect to a SQL driven Visual Basic application on a Windows Domain

Is this application on Linux, or Windows?

Please give more information, your questions are vague.

---

### Post by jkarns on 2007-08-29
Well, the application is ran in Windows right now...but I am trying to get it to work on Ubuntu. I need it to be able to work on both. We have over 100 machines now that run it on Windows, but will be purchasing 40-50 new machines that I would like to use Ubuntu on instead. 

I have installed it with WINE and Crossover. But, when I try to run the app, I get the error: 

Run-time error '429':
ActiveX component can't create object.

---

### Post by LaRoza on 2007-08-29
> **jkarns said:**
> Well, the application is ran in Windows right now...but I am trying to get it to work on Ubuntu. I need it to be able to work on both. We have over 100 machines now that run it on Windows, but will be purchasing 40-50 new machines that I would like to use Ubuntu on instead. 

I have installed it with WINE and Crossover. But, when I try to run the app, I get the error: 

Run-time error '429':
ActiveX component can't create object.

VB is best suited for Windows programming, and is even then a poor language. If you need MS SQL Server, use Windows.

You can connect to MS SQL Server with Linux, if that is what you want to do.

---

### Post by jkarns on 2007-08-29
OK, yes...that is what I want to do. The fact is, the IT guy that was already here when I started here wrote this software using VB. I am not debating if it is good or bad programming language...Windows or Linux. It's done that way...and it has to stay that way. 

What I want to figure out, is  can I make this application work on Ubuntu? If I get this error when I run it...is there a fix? 

Run-time error '429':
ActiveX component can't create object.

---

### Post by LaRoza on 2007-08-29
> **jkarns said:**
> What I want to figure out, is  can I make this application work on Ubuntu? If I get this error when I run it...is there a fix? 

Run-time error '429':
ActiveX component can't create object.

I don't know if you can make the application work in Linux, sorry.

---

### Post by Shin_Gouki2501 on 2007-08-29
u "could" try mono, good luck though...
also u should rename ur thread, its not an "SQL" Issue but an VB on Linux issue i guess..

---

### Post by LaRoza on 2007-08-29
> **jkarns said:**
> I am looking to impress the boss and save a ton of money by converting to Ubuntu. 

This could cost more in the long run, although Linux, MySQL, and the languages are free, the time and effort is a real cost.

Changing an existing system is *much* harder than maintaining.

---

### Post by KCPokes on 2007-08-29
By default I don't believe you can run VB within Linux.  Of course a quick search shows some success running via Wine or via a bridge software called REALBasic.

---

### Post by deadgobby on 2007-08-29
My I give some advice. Read up on this link

[http://www.mysql.com/](http://www.mysql.com/)

Gobby

---

