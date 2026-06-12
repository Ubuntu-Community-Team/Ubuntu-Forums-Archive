---
title: "Folder Creation Question"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by indytim on 2006-03-15
I just configured LAMP per the WIKI and everything is working well.  It is now time to load up the development web server.  I need to be able to freely add libraries (in the form of folders and files) under the web server root (/var/www ).  Using the Nautilus file manager, I found out that the root web server directory is a root-owned folder.  I did the predictable "Windows" approach and did the right mouse--click to properties and found that I was locked out from creating folders in the directory.

I've done a cursory search of the WIKI and haven't found anything definitive on setting the permissions permamently on the /var/www folder. I'm sure it's something very basic, but just missing it at the moment.

Thanks,

IndyTim

---

### Post by gord on 2006-03-15
```
sudo chown <user> <directory>
```

that changes the permitions of any given directory, for example i would do
sudo chown gord /var/www

im not sure how advisable it would be to change the owner of that particular directory though.

---

### Post by Spark* on 2006-03-15
It's not pretty, but you could launch Nautilus with administrator rights to do this. Just type "sudo nautilus" in a terminal. Hopefully Nautilus will be able to gain administrator rights on demand at some point.

The traditional way would be to change the permissions using "chmod" from the CLI... To change the owner you could do a "sudo chown username:username /var/www".

---

### Post by garretjax on 2006-03-15
The folder /var/www would have been created when you installed apache; most likely by the root account.  The reason you cannot directly change the rights to it through nautilus, is that you are working under you user account - whatever you call it, and you don't have rights to superseed the current priviledges.
Its sometimes hard to explain in text, but if you think of it in military rank, you have to be as high or higher to change permissions on someoneleses directory, and nobody outranks root.


anyway, enough of the lecture - what you need to do is change to owner/group of the /var/www directory 

Open a terminal and this should do the trick - note user and directory might be reversed, i can never remeber which way it goes - if you have it backwards the shell will tell you no such directory. subsitute what is in [] for what it is in your case

sudo chown [user] [directory]   
sudo chgrp [group] [directory]    

What user/group you change this to should be decided on how secure you want it to be - i'm thinking group/user www and then make you account a member of that group - that way you have access, and set any account that should have ftp access to create directories within that folder to also be a member of www

Admittedly i've never set up a LAMP system, so i dont know what security restrictions you may want to work under

Hope this makes sense,
T

---

