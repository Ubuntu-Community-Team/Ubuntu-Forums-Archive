---
title: "apache trouble with permissions"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by ejbrever on 2006-12-03
Hi, I am creating a webpage that will link to a document server and I am having permissions issues.

I mounted another file server to /var/www/files. I chmod'd everything to 777. When I try and go to the directory I get: 

"You don't have permission to access /files/ on this server.
Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request."

Does anyone know why this is? Is there a setting I'm missing?

Thanks,
Eric

---

### Post by sardion on 2006-12-03
Make sure the whole path is world readable and executable, i.e.

chmod a+rx /var
chmod a+rx /var/www
chmod a+rx /var/www/files
chmod a+r /var/www/files/*

Also make sure the whole path to your error pages are world readable (and executable for directories).


ALternatively, a more complicated but better from a security standpoint point of view (if there are any other users on the server) would be to change the group of all the files and directories involved to be www-data

i.e.
chgrp www-data /var/www

and so on, and make all the files/dirs group readable (and executable).


If this still doesn't fix the problem, attach your httpd.conf file.

---

### Post by dujlinvik on 2006-12-28
i'm newbie in Ubuntu and having similar probleme with Apache (it's probleme TO ME because i don't know how to fix it...).
i'm working on a site and copied it to ....../apache2/htdocs/mysite
result in firefox is :
[SIZE="5"]"Forbidden

You don't have permission to access /mysite/index.php on this server."[/SIZE]

i tried to find some related text on apache.org, without success..........
any help is appreciated

---

### Post by pseudologically on 2006-12-30
> **ejbrever said:**
> Hi, I am creating a webpage that will link to a document server and I am having permissions issues.

I mounted another file server to /var/www/files. I chmod'd everything to 777. When I try and go to the directory I get: 

"You don't have permission to access /files/ on this server.
Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request."

Does anyone know why this is? Is there a setting I'm missing?

Thanks,
Eric
I've reproduced you error:

> **Forbidden**

  You don't have permission to access /new file on this server.

Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.The problem seems to be that Apache doesn't have permission to access that file or directory (duh, eh?).

I'm assuming you created that file since that's what I did. If so, that file's/directory's owner is you, the creator. You could do as sardion suggested and create a new group for www-data, add the root user and yourself to the group, and chgrp the files/directories and give that group wrx permissions.

I'm new to this also, so if there is an easier way, please, people, don't hold yourself back!

:-D

---

### Post by sardion on 2006-12-30
I'm assuming you created that file since that's what I did. If so, that file's/directory's owner is you, the creator. You could do as sardion suggested and create a new group for www-data, add the root user and yourself to the group, and chgrp the files/directories and give that group wrx permissions.


The group www-data is created automatically when apache is installed.

The "right" way to do this is to use chgrp as I stated above.  The quick and dirty hack is to make everything be chmod a+rx.

If my above post does not clear up how to do this, let me know what exactly you are having trouble with.

---

### Post by pseudologically on 2006-12-30
Is the group www-data hidden? When I open System > Administration > Users and Groups, I don't see it listed.

Also, does Apache run as root?

Thanks!

---

