---
title: "how to change permisions on a folder"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-06-08
I need to change the following permission on a folder so that ampache can access it

i thought it went sudo chmod r+rw /home/mike/test

but that ain't working i need to allow ampache access to it

---

### Post by taurus on 2006-06-08
Before you make any changes to /home/mike/test, you want to make sure /home/mike has the right permissions first!!!  So
```

chmod 777 /home/mike
chmod 777 /home/mike/test

```

---

### Post by _simon_ on 2006-06-08
Not sure how you do it that way... I installed "Nautilus Scripts" via Automatix.

That gives you a script menu in nautilus (right click) which will open folders and files as root and then you can change the permissions that way.

---

### Post by BoyOfDestiny on 2006-06-08
To make it recursive
chmod 777  -R /home/mike/blah/

---

### Post by hajk on 2006-06-08
The preferred way of making files available in Apache is to put them in the 
/var/www directory, you need to do this with sudo. If you don't want to put the 
actual file in this directory, then you should (again with sudo) put a symlink to it 
in the /var/www directory: for example "sudo ln -s /home/mike/test /var/www/test".

(But seriously, do you want to give the whole world wide web write access to that file?)

---

### Post by lime4x4 on 2006-06-08
well this ubuntu box is behind a ipcop firewall/router box and it's only for a mp3 server for the house no net access.. And the app that needs access to that folder is ampache..Thanks for all the replies

---

### Post by cjssmo on 2007-08-27
hajk

Actually on Ubuntu and Debian, the preferred way of installing ampache is into /usr/share and then make ampache available via a virtual host in /etc/apache2/conf.d this way you music is not in the web root.  then when you build your catalogs you can point to a location also outside of your web root.  Where ever you have your music, this location needs to have read/write permissions.

Regards

Charlie  :)

---

