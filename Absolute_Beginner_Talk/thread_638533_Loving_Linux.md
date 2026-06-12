---
title: "Loving Linux"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by finito on 2007-12-12
I Love how linux works, I have even installed linux on my computer at work. I have everything. I own my own company, I made my own software for work since I made it on Windows using C# I thought why not use MSSQL (at first I was using MSAccess but I had too mnay users so I switched). Now I need to use MS SQL Studio from time to time so I have a dual boot setup, is there a Program that does everything that MSSQL Studio does for Linux or should I use Wine, my other otion would be to move to MySQL but the mere thought of it kills a few brain cells. I know what I will have to do to rewrite it but I want to keep that as the last possible solution.

any help would be nice.

---

### Post by kevinatkins on 2007-12-12
Hi,

I migrated a MS Access database to MySQL as the backend, but still using Access as a client, connecting via ODBC. I can attest it was rather a lot of work and quite a few niggly problems cropped up, but now it's working nicely.

If you've been using C# / SQL Studio on Windows, then here on Linux, Mono springs to mind. It's an open-source implementation of .net, largely compatible I believe, but I'm not really familiar with it myself.

---

### Post by finito on 2007-12-12
I also have heard of Mono, but I am not worried bout that I am more worried about SQL studio...

---

### Post by hyper_ch on 2007-12-12
What does MS SQL Studio do?

---

### Post by finito on 2007-12-12
MS SQL Studio = Microsoft SQL Management Studio. Mainly I use it to get raw data from the tables (edit Rows and add rows). I can also edit Table Layouts (Relationships, primary key,  add  and remove columns, etc). Those are the two main functions I need.

---

### Post by ByteJuggler on 2007-12-12
> **finito said:**
> MS SQL Studio = Microsoft SQL Management Studio. Mainly I use it to get raw data from the tables (edit Rows and add rows). I can also edit Table Layouts (Relationships, primary key,  add  and remove columns, etc). Those are the two main functions I need.

I'm pretty sure that types of functions for MySQL would be covered by MySQL administrator, MySQL query browser and/or MySQL Workbench, all of which is GUI tools. Anyway, you could try to run MSSQL Management studio under "Wine", although I have no idea whether it'd work.

Edit: There's also "SQLYog" which seems really good : [http://www.webyog.com/en/screenshots_sqlyog.php](http://www.webyog.com/en/screenshots_sqlyog.php)

---

### Post by finito on 2007-12-12
I don't think those will work with MSSQL. I don't know a lot about the differences with MySQL and MSSQL but I do know this that they store a few varible type differently.

---

### Post by ByteJuggler on 2007-12-12
> **finito said:**
> I don't think those will work with MSSQL. I don't know a lot about the differences with MySQL and MSSQL but I do know this that they store a few varible type differently.

I did not say they would work with MSSQL, I simply tried to show that MySQL has similar tools comparable with MSSQL's Management studio available for it.

So if your primary objection/problem with moving to MySQL happens to be the availability of a tool ***like ***MSSQL Management Studio, then equivalents actually exist on MySQL.

(Aside: To be clear, those tools are MySQL tools, and will NOT work with MSSQL. )

---

### Post by finito on 2007-12-12
I would love not to move to MySQL as I said last solution. bah I will try and install through wine.

what I was looking for was a replacement of MSSQL Studio.

---

### Post by HermanAB on 2007-12-12
So install Vmware with WinXP, then you can run Windows in a window and still use the MS Studio program to support your MS schtuff.

---

### Post by hyper_ch on 2007-12-12
ever had a look at phpMyAdmin? It's browser based but an excellent tool for mysql.

---

