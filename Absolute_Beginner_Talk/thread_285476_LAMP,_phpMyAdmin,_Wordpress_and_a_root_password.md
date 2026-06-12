---
title: "LAMP, phpMyAdmin, Wordpress and a root password"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by DarkKoopa on 2006-10-26
Hi,

I installed a LAMP server with a GUI and the installed phpMyAdmin and then wordpress.

Great for my wife, she now has a local blog that the family can look at.

But on the phpMyAdmin page, there is this message down the bottom

> Your configuration file contains settings (root with no password) that correspond to the default MySQL privileged account. Your MySQL server is running with this default, is open to intrusion, and you really should fix this security hole.

Do I need to give the root user a password? I thought that Ubuntu didn't have a root user account.... or is the account for MySQL different and it does exist??? :-k 

I want to make it secure, but I don't want put a password on the root account and then not have the wife be able to use wordpress or her family access it....
I'd be dead...  :-({|= 

Any help in baby steps would be appreciated.

---

### Post by az on 2006-10-26
> **DarkKoopa said:**
> 
I want to make it secure, but I don't want put a password on the root account and then not have the wife be able to use wordpress or her family access it....
I'd be dead...  :-({|= 

Any help in baby steps would be appreciated.

See here:
[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

The mysql root is not the same as the root account.  You need to set the mysql root password so that not just anybody can log into your mysql database.

You should also not let any web application use the mysql root user, but create another mysql user with fewer priviledges.

---

### Post by DarkKoopa on 2006-10-27
I have a serperate account/user for wordpress, so I guess I was lucky and thought ahead there.

I have made passwords for the 2 root accounts that existed...

root@localhost
root@ubuntu (the machines network name)

I did this through phpMyAdmin (before I saw your post)....

I never had to do this when I installed wordpress

> sudo ln -s /etc/wordpress/config-localhost.php /etc/wordpress/config-hello.homelinux.net.php


I'm running version 2.0.4......

---

### Post by Leec on 2006-11-10
In trying to install WordPress I get the following error:

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

when I try to do the   mysql -u root
any ideas.  I have not been able to use MySqlAdmin to log in to the database either since I installed Darper Drake.  

Also have the following error when I go to localhost/wordpress/

Forbidden

You don't have permission to access /wordpress/ on this server.

Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.

Anyone......please
Lee

---

