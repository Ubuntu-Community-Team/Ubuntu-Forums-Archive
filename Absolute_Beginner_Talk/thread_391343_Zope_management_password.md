---
title: "Zope management password?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by gravz84 on 2007-03-23
****RESOLVED****
Hi,
I installed plone 2.5.2 using the unified installer & now I can't get into the zope management interface.
I don't even remember if the installer prompted me for a username and password for zope..i don't think it did.
Now I can't go into zope management because its asking for the username and password. The file I am supposed to look at -adminPassword.txt won't open-it says 

"Could not open the file /opt/Plone-2.5.2/adminPassword.txt" You do not have permissions necessary to open the file"

Infact the whole Plone folder is not owned by root or my own username rather it shows under permissions owner as "plone".
Since i am not the owner, I cant change permissions or even delete the folder to reinstall zope!! 
Anyone know if there is a default usrname passwd generated with the unified installer?? What can I do if I want to change the password?

---

### Post by gravz84 on 2007-03-23
Nevermind.. i changed the ownership of the folder and file and now can read the text file containing username and password.

---

