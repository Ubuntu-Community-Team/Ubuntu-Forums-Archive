---
title: "Xampp - don't have permission to access new folder"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by jnorris235 on 2008-01-08
Xampp works perfectly - there is a link to my own www folder (~/www) in /opt/htdocs
localhost/~ works fine.

I moved that www folder to my Desktop, created a new link in /opt/htdocs to
~/Desktop/www
and now I'm told I don't have permission to access it.
Why not?
These permissions do seem weird, changing as they do!

---

### Post by gate on 2008-01-08
Actually, there is a variable called a umask (I think) which dictates how permissions are inherited.

  What are you trying to access that tells you permission denied? if it is the www on your desktop (that is *very* weird) you can run "chmod 755 ~/Desktop/www", if it is the symbolic link, make sure that the link points to the right location, if it does then "chmod 777 /opt/htpdocs/[linkname]"

---

### Post by unabatedshagie on 2008-01-10
I'm having a similar problem.

Just freshly installed gutsy and downloaded the latest version of xampp (1.6.5a), "installed" fine and works fine.

Now previously I have been able to run the following command```
sudo ln -s /home/alex/WebDesign /opt/lampp/htdocs/%USER
``` and type **localhost/alex** into firefox to view the files in the folder.

Now I'm getting an error saying that I don't have permission to access the files on the server.

As far as I can tell I have the correct permissions on the folder (I haven't changed the permission on the WebDesign folder since I backed it up and restored it)

---

### Post by jnorris235 on 2008-01-10
It seems for me that doing any Konsole/Terminal commands didn't work.
But I just learned about Sharing by right clicking in Places/Homefolder AND then checking it in System/Shared folders. i have found that doing it in one doesn't necessarily lead to it showing it in another. Check 'em all!
Cheers guys.

---

