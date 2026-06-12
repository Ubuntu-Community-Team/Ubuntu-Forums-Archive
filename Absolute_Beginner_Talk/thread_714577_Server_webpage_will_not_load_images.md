---
title: "Server webpage will not load images"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Rafiki123 on 2008-03-03
I've recently been trying to create a webpage for my apache server but I can't seem to figure out why my images are not loading on the page. I know that the index.html has the proper code for an image in the home directory and I even tried using a link to a 3rd party image and that didn't work either. I think it maybe has something to do with the permissions to acess images on the server?

Any help would be most appreciated :)

---

### Post by jan quark on 2008-03-04
try to change the permissions of the images to 644 -rw-r--r--
[http://www.zzee.com/solutions/chmod-help.shtml](http://www.zzee.com/solutions/chmod-help.shtml)

---

### Post by Rafiki123 on 2008-03-04
Is there a way I can change the folder's permissions, or do I have to chmod every file?

---

### Post by Rafiki123 on 2008-03-04
I tried to chmod 644 the picture and it did not make it appear in the webpage. What kind of permissions should my index.html file have? Because when I type in the address of an image insted of the image on the server, it won't show up either.

---

