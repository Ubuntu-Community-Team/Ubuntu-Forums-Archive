---
title: "[SOLVED] Finding Apache, php, mysql"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by DaveyG on 2007-03-11
Hi, i installed Ubuntu (Edgy Eft) 6.10 today to use as a web server, i used Synaptic Package Manager to install the necessary components, Apache, php ect...
Everything is working fine, but i cant find the Apache folder were everything is stored
i.e if you go to Daveyonline.net it shows the holder page, i cant find were that is.
can anyone point me in the right direction?

(Sorry for my bad english)

Thank you, Davey

---

### Post by v8YKxgHe on 2007-03-11
It should be in /var/www. Also - you may want to check these guides out:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

---

### Post by DaveyG on 2007-03-11
Thanks for your help Alex, il be sure to check them out right away.

---

### Post by DaveyG on 2007-03-11
Now that iv found the files, i dont seem to be able to delete them as i dont have permission :confused: I think im set as the admin....

---

### Post by black_ice on 2007-03-11
U can easily install and work with them by using the ultimate package XAMMP from the apache friends site >> [www.apachefriends.org](www.apachefriends.org)

---

### Post by DaveyG on 2007-03-11
I still dont understand... all i want to do is delete the files.. but wont let me coz i dont have permission, how do i change the permissions?

im beginning to regret using ubuntu :icon_frown:

---

### Post by atraeyu on 2007-03-11
In ubuntu there is no root account - so your account doesn't have "root" access.  However, you can run any command from the terminal with root access by typing "sudo" before the command.

For example, earlier I needed to edit my /etc/hosts file.  If I navigate to that file in gnome and then open it and try to edit it, I get an error message that I don't have access.

However, if I open a terminal and type "sudo gedit /etc/hosts" it opens the /etc/hosts file in gedit with root access - and I can edit and save.

I don't know if there is a way to open files from gnome with root access ...

---

