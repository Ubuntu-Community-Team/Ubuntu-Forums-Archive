---
title: "[SOLVED] Fill In The Blanks"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-01-27
haha.
so i finally got my php and mysql and everything working together.
now what do i put in these blanks?
i installed LAMP server from synaptic package manager if that makes any difference.

---

### Post by PeterJS on 2008-01-27
Assuming it's all running on one machine, the host name would be localhost, the port would be blank for use default. The DB name, username, and password are whatever you set them up to be. If you haven't set that up already, you might want to install phpMyAdmin to make setting the database and account easier.

---

### Post by RadiationHazard on 2008-01-27
how might i go about installing phpMyAdmin and setting all that up?

---

### Post by RadiationHazard on 2008-01-27
Ok, I used 

```
sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin
```

to install phpmyadmin and I selected apache2 when it said "Web server to reconfigure automatically:"

so i'm pretty sure it's all set up now.

but how do i open phpmyadmin so that i can set my username and pass?

---

### Post by emarkd on 2008-01-27
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

### Post by RadiationHazard on 2008-01-27
ok, this is really starting to annoy me!!!
i whipped my whole hard drive and reinstalled linux so that i could start over because i taught i'd done something wrong cause for some reason whenever i started going to look at my site a thing kept popping up asking me to download something called a "PHTML file" and i don't know why or how to make it stop so that i can freaking build my page!
please someone tell me that you know what's wrong and how to fix it???

---

### Post by emarkd on 2008-01-27
Your server is not parsing php pages.  Instead it's offering them for download.  Is it doing this when you try to go to your phpmyadmin?

---

### Post by RadiationHazard on 2008-01-27
yeah. :(

---

### Post by emarkd on 2008-01-27
I know you said that you removed all those server packages you installed and reinstalled using the Task in Synaptic, but did you remove them using the --purge option?  Like this:

```
sudo apt-get remove --purge packagename
```

If you don't do the purge, apt will leave the config files behind and when you reinstall some bad config data can be left over.

---

### Post by Kilz on 2008-01-27
To get apache to show php files instead of offering them to download. Open a terminal and type in this
```
sudo gedit /etc/apache2/apache2.conf
```
The editor will open the apache configuration file. At the bottom of the file type this in
```
AddType application/x-httpd-php .php .htm .html
```
Then save the file. Restart apache, or reboot.
If you want to have php index files, search the config file for this line
```
DirectoryIndex index.html index.cgi 
```
Add index.php to the list.

---

### Post by RadiationHazard on 2008-01-27
Ok, so i reinstalled ubuntu and started over. I have already installed LAMP Server and need to kow what do next. please someone help me finish setting up my server with phpbb on it.

---

