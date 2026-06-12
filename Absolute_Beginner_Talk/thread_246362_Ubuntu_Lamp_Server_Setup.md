---
title: "Ubuntu Lamp Server Setup"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by clee on 2006-08-29
Hello, i would like to set up the apache server so that the users that login with ftp can upload the website and so that it is hosted stright away, when the users connect it goes to there home dir how can i change that so the users home dir is /var/www/hosted/"there usernamehere" and protect it so they can not see any other files exept from there space or is there any other better ways of doing it?:confused:

---

### Post by noumaan on 2006-08-30
You would find some quick tutorials [here]("http://httpd.apache.org/docs/").

---

### Post by Bachstelze on 2006-08-30
You can use [http://yourserver.org/~user](http://yourserver.org/~user) which will run the webserver on /home/user/public_html. So the users just have to create a public_html subdir in their home and put their files in there.

---

