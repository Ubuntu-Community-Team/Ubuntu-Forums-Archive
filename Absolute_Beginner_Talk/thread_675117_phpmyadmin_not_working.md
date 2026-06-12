---
title: "phpmyadmin not working"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-01-22
I installed LAMP with synaptic package manager / then phpmyadmin, but it is not working if accessing localhost/phpmyadmin - what do u recommend?

---

### Post by PeterJS on 2008-01-22
What happens? Is it a file not found error? the casing on it is usually: php**M**y**A**dmin.

---

### Post by ben22 on 2008-01-22
no it's not working with that writing either.

the problem is that the folder phpmyadmin is not in the var/www folder, but in usr/share - I somehow will have to configure apache config file to use it, but i have no clue what to do nor did I find a good documentation

---

### Post by PeterJS on 2008-01-22
Funny that the installer didn't take care of that for you. Why fight the config files when you can just symlink the phpMyAdmin folder in to /var/www:
```

sudo ln -s /usr/share/phpMyAdmin /var/www

```

---

### Post by ben22 on 2008-01-22
hi Peter,

unfortunately this did not help.

Should i just remove the complete LAMP installation with:

**sudo apt-get remove apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql && sudo apt-get autoremove**

and then reinstall with

**sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql**

or find the error - maybe someone else runs into the same problem later.

Best,
Ben

---

### Post by ben22 on 2008-01-22
hm - in the www folder it says that the link to phpmyadmin is broken

---

### Post by PeterJS on 2008-01-22
> **ben22 said:**
> hm - in the www folder it says that the link to phpmyadmin is broken

I made (an apparently bad) assumption about where phpMyAdmin was, look for it and use the right path.

---

### Post by ben22 on 2008-01-22
Hey Peter,

the location was right only that the folder uses lower case letters - thus it didnt find it...

it's working now!! yeahh!!

I also like the idea to create a folder in home - though I did not really understand what I have to do - could u post step by step instructions here: [http://ubuntuforums.org/showthread.php?t=675115&page=2]("http://ubuntuforums.org/showthread.php?t=675115&page=2") 

again, thanks a lot for the help!

cheers 
Ben

---

### Post by PeterJS on 2008-01-22
> **ben22 said:**
> Hey Peter,

the location was right only that the folder uses lower case letters - thus it didnt find it...

it's working now!! yeahh!!

I also like the idea to create a folder in home - though I did not really understand what I have to do - could u post step by step instructions here: [http://ubuntuforums.org/showthread.php?t=675115&page=2]("http://ubuntuforums.org/showthread.php?t=675115&page=2") 

again, thanks a lot for the help!

cheers 
Ben

It's the same idea as setting up the symlink for the phpMyAdmin, but using the path to the folder you want to share in your home directory instead, as for permissions as long as the folder is world readable and executable, and the files are world readable you should be good to go.

---

### Post by Mission 10 on 2008-01-23
> **PeterJS said:**
> Funny that the installer didn't take care of that for you. Why fight the config files when you can just symlink the phpMyAdmin folder in to /var/www:
```

sudo ln -s /usr/share/phpMyAdmin /var/www

```

Great advise, worked for me. It's silly that Synaptic doesn't copy the folders to /var/www automatically. But this was an easy fix, thanks.

---

### Post by mohbana on 2008-01-27
> **PeterJS said:**
> Funny that the installer didn't take care of that for you. Why fight the config files when you can just symlink the phpMyAdmin folder in to /var/www:
```

sudo ln -s /usr/share/phpMyAdmin /var/www

```

Thanks, this needs to get fixed before new version comes out.  funny that installer doesnt take care of it

---

### Post by tonydm on 2008-01-29
I've got a question regarding this same problem.  I too found phpMyAdmin was installed in /usr/share/phpMyAdmin.  I have a server install w/o a GUI.  I use putty to access the server and webmin.

I tried the sudo ln -s /usr/share/phpMyAdmin /var/www and it created the symlink.  The rights to the link are 0777 and the /usr/share/phpMyAdmin directory is 0755. 

When I go to [http://172.16.0.11/phpMyAdmin](http://172.16.0.11/phpMyAdmin) I get a 403 Forbidden response.  For clarification, I must access my server from another workstation.  I cannot use localhost.

tonydm

---

### Post by mohbana on 2008-01-29
This should fix it, it did it for me.

Select apache2, by pressing the*** space bar*** then press ***TAB*** then ***enter.***  Note it probably didn't get setup probably intially because you didn't press the space tab, this happend to  me.

> sudo dpkg-reconfigure phpmyadmin


Restart apache, if the [http://localhost/phpmyadmin](http://localhost/phpmyadmin) still doesn't work.  I believe you can login with any username and password you've setup with mysql.

> sudo ln -s /usr/share/phpmyadmin /var/www



I no longer have to resort to this approach.

> sudo ln -s /usr/share/phpmyadmin /var/www


---

### Post by tonydm on 2008-01-30
Just looking for anyone to take another look at this post.  Any help would be great!  Thank you

tonydm

---

### Post by Jonian on 2008-02-08
bad post , sorry.

---

### Post by Liesmith Loki on 2008-02-27
> **mohbana said:**
> This should fix it, it did it for me.

Select apache2, by pressing the*** space bar*** then press ***TAB*** then ***enter.***  Note it probably didn't get setup probably intially because you didn't press the space tab, this happend to  me.



Restart apache, if the [http://localhost/phpmyadmin](http://localhost/phpmyadmin) still doesn't work.  I believe you can login with any username and password you've setup with mysql.




I no longer have to resort to this approach.
Excuse me, but I seem to be having the same issues as you had. However, before I came to the reconfiguration solution that you provided (I forgot to select it too. xP), I used your ln command to create a link to the phpmyadmin folder in /usr/share. Now whenever I link to [http://localhost/phpmyadmin](http://localhost/phpmyadmin), I get a dialog box that asks me how I should open a PHTML file, or if I should download it. Also, I notice that there still is no phpmyadmin folder in my /var/www. Can anyone please help me with this?

I've uninstalled and reinstalled all the components of apache2, phpmyadmin, and mysql a number of times.

---

### Post by Liesmith Loki on 2008-02-27
> **Liesmith Loki said:**
> Excuse me, but I seem to be having the same issues as you had. However, before I came to the reconfiguration solution that you provided (I forgot to select it too. xP), I used your ln command to create a link to the phpmyadmin folder in /usr/share. Now whenever I link to [http://localhost/phpmyadmin](http://localhost/phpmyadmin), I get a dialog box that asks me how I should open a PHTML file, or if I should download it. Also, I notice that there still is no phpmyadmin folder in my /var/www. Can anyone please help me with this?

I've uninstalled and reinstalled all the components of apache2, phpmyadmin, and mysql a number of times.

Can anyone help me with this?

---

### Post by The MacNab on 2008-03-02
Notice that in the troubleshooting section for installing PHP while configuring a ubuntu LAMP server, there is a discussion about exactly this problem of not rendering the PHP files:

[https://help.ubuntu.com/community/ApacheMySQLPHP#head-6ce180906ddbc141ef4b213f82465515a8ad3031-2](https://help.ubuntu.com/community/ApacheMySQLPHP#head-6ce180906ddbc141ef4b213f82465515a8ad3031-2)

---

