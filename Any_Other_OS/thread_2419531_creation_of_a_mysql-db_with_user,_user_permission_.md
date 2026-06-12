---
title: "creation of a mysql-db with user, user permission - which is the correct sequence"
date: 2019-05-23
forum: Any Other OS
---

### Post by dilbert_one on 2019-05-23
good day dear experts hello dear Ubuntu-frineds, 

well - i mused bout the right place to post this question:  Finally i decide to put it into this forum - any other OS ... probably it fits most here. 



i am running webmin  


now for the creation of a mysql-db  with user, user permission and so on.. 
which are the right steps and whhich is the correct sequence - 


in other words:  what comes first - second - third ... 


btw: some of the net-ressources say like so;: 
[https://www.trustfm.net/ebooks/DedicatedServer.php?page=MySQL](https://www.trustfm.net/ebooks/DedicatedServer.php?page=MySQL)


first: Now go to Servers > MySQL Database Server. 
Click the "Start" button in order to start the database server.
Now click the link "Create a new database".


next ...: create a new "User" 


third:...After the user creation Webmin will lead you at the "User Permissions" page where you should have the newly created user userwebsite1db1 like the picture below. 


forth: .. click at the "Return to database list" list located at the bottom of the page. 


Finally we have to assign the userwebsite1db1 user at our website1db1 database.
Click at the "Database Permissions" icon. Hit the link "Create New Database Permissions." 
> 
> Now fill the "Create Database Permissions" form like this : 
> Databases : selected website1db1 
> Username : userwebsite1db1 
> Host : localhost 
> Permissions : ALL (use the CTRL key in order to enable multi-select)
> 
> Hit the "Create" button. 


and subsequently ... click at the "Return to database list" list located at the bottom of the page. 
At this point we have finished with MySQL setup and configuration.


questions that arise: 
- is it correct to use the db first or shouldnd i create a user at the first step!? 
- what if i enter in the Create-DB-Section 
~~~
Host: [] from Host Permission  []  Any [] .... what if i choose here any instead of localhost
~~~


Question: can this be done!? Is it possible to choose here any and afterward in the credentials of the setup of - eg a wordpress site - i can choose localhost? 




love to hear from  you

---

