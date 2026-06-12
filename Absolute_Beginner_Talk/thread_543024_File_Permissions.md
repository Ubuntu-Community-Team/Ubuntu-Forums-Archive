---
title: "File Permissions"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Amalgamayne on 2007-09-04
Hello:

I have a question about file permissions for my desktop.  I have put a portfolio up on my apache2 server, but I can't see anything that are in any subdirectories.  It gives me 403 errors.  I was wondering if anyone can help me enable people to view these folders, as they contain my images and websites that I have made.  Here's the result of ls-l:

-rwxr--r-- 1 root root   602 2007-09-04 16:22 casey.css
-rwxr--r-- 1 root root  6263 2007-09-04 16:23 contact.html
drwxr--r-- 2 root root  4096 2007-09-04 16:20 Downloads
drwxr--r-- 2 root root  4096 2007-09-04 16:21 images
-rwxr--r-- 1 root root  7987 2007-09-04 16:23 index.html
drwxr--r-- 2 root root  4096 2007-09-04 16:21 Music
-rwxr--r-- 1 root root 15725 2007-09-04 16:24 music.html
-rwxr--r-- 1 root root  6120 2007-09-04 16:24 portfolio.html
-rwxr--r-- 1 root root 10778 2007-09-04 16:24 programming.html
-rwxr--r-- 1 root root   209 2007-09-04 16:24 resume.html
-rwxr--r-- 1 root root 12186 2007-09-04 16:24 web.html
drwxr--r-- 7 root root  4096 2007-09-04 16:22 WebWork

Thanks for your help!

---

### Post by dwhitney67 on 2007-09-04
There is nothing wrong with the permissions, although I would recommend that you strip away the unnecessary "execute" permission from each of the HTML files.  To do that, run this command:

[FONT="Courier New"]$ sudo chmod -x *.html[/FONT]

Also, I do not know how you configured your Apache server.  Can you give insight into this?  Are your folders outside of the /var/www area?  If so, you need to follow the instructions available at this site:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_map_URLs_to_folders_outside_.2Fvar.2Fwww.2F](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_map_URLs_to_folders_outside_.2Fvar.2Fwww.2F)

---

### Post by schorsch on 2007-09-04
If the output of the "ls -l" command shows the directory listing of /var/www (the standard DocumentRoot of an apache server running under Ubuntu) all those files should belong to the user under which the apache server is running and not root. Normally this will be the user "www-data" and the group "www-data" except you changed something in your apache config.
You can check the user with
```
ps -ef|grep apache
```

---

### Post by Amalgamayne on 2007-09-04
Thanks for the advice.  It turns out that everything is was in /var/www, but i didn't have the ownership of the folder and the group to be www-data.  Something else I learned today! Thanks.

---

### Post by Paul133 on 2007-09-04
Would this work? ```
sudo chown www-data:www-data *
```

---

### Post by dwhitney67 on 2007-09-04
> **Amalgamayne said:**
> Thanks for the advice.  It turns out that everything is was in /var/www, but i didn't have the ownership of the folder and the group to be www-data.  Something else I learned today! Thanks.
That's something I have learned too.  I have a personal web-server using Apache/2.2.2 and none of my HTML or uploadable files have the user or group names assigned to www-data.  My files are all owned by root, and in my case, everything works fine.

---

### Post by schorsch on 2007-09-05
If your web server is running under "root" (which is not really adviseable ....) you will not get any problems. Have you checked the owner of the apache process?

---

### Post by hyper_ch on 2007-09-05
default apache install has directory listing turned off... so you will need to alter that in the apache config or, if you can overwrite those settings, create a .htaccess file that will contain the according command.

---

