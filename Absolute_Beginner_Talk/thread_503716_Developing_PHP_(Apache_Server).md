---
title: "Developing PHP (Apache Server)"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Snitz on 2007-07-18
As I know, Ubuntu comes with a built in Apache Server (php, mysql), so how can I access it and browse my sites locally?

And what software can I use similar to dreamweaver that can help me developing PHP Application with a preview channel and all?

---

### Post by Majorix on 2007-07-18
I am not sure if you are correct. Cause I had to install LAMP manually on my Ubuntu installation.  Anyways here is how to do it:
```

sudo apt-get install apache2
sudo apt-get install libapache2-mod-auth-mysql
sudo apt-get install libapache2-mod-php5
sudo apt-get install mysql-client-5.0
sudo apt-get install mysql-server-5.0
sudo apt-get install php5
sudo apt-get install php5-mysql
sudo apt-get install phpmyadmin

```

Also, have you tried NVu?

---

### Post by Snitz on 2007-07-18
Whenever I type this one
> sudo apt-get install apache2
It asks me to inset the Ubuntu CD and press Enter. I do it and it keeps on asking me the same thing.
And what's NVU?

---

### Post by Snitz on 2007-07-18
Ah never mind, it worked. I had the wrong CD inserted.
What's NVU?

---

### Post by Majorix on 2007-07-18
Its basically a web developing editor with the preview feature you want. You can learn more from their site:
[http://www.nvu.com/index.php](http://www.nvu.com/index.php)

---

### Post by mlentink on 2007-07-18
You might want to also take a look at Bluefish

Edit: I might add that NVu is not really actively developed anymore (latest ubuntu release if for 5.04...) and there is a bunch of people that claim they are continuing it: [Kompozer]("http://www.kompozer.net/")

---

### Post by Majorix on 2007-07-18
Does Bluefish have the preview feature?

@Snitz:
Please note that NVu is not in the repos for some reason. You will have to install it manually if you want to.

---

### Post by Snitz on 2007-07-18
I'm still installing the LAMP server manually, however, I'm getting this error in the Terminal when I reached the mysql-server-5.0

> sudo: timestamp too far in the future: Jul 18 08:32:37 2007
snitz@root:~$ sudo apt-get install mysql-server-5.0
sudo: timestamp too far in the future: Jul 18 08:32:37 2007
snitz@root:~$ sudo apt-get install php5
sudo: timestamp too far in the future: Jul 18 08:32:37 2007


---

### Post by Majorix on 2007-07-18
I would suggest reading this topic:
[http://ubuntuforums.org/showthread.php?t=173505](http://ubuntuforums.org/showthread.php?t=173505)

---

### Post by Snitz on 2007-07-18
It seems that I got the error after I changed the time. I restarted and continued downloading.
So, after finishing the download when I want to see my sites locally, I just goto [http://127.0.1.1/phpmyadmin](http://127.0.1.1/phpmyadmin) or mysite?

---

### Post by mlentink on 2007-07-18
@Majorix: Bluefish uses external browsers for preview, you can define which one

You timestamp problem: are you getting these files form a local source or form something in a completely different timezone? I must admit to not having seen this before...

---

### Post by Majorix on 2007-07-18
Well basically you go to [http://localhost/index.html](http://localhost/index.html) to see if your installation went ok. Then you can add your files under /var/www/apache2-default .

---

### Post by Majorix on 2007-07-18
> @Majorix: Bluefish uses external browsers for preview, you can define which one

Oh I didn't know about that... Good feature. I will give it a go in the near future :)

---

### Post by jn25b on 2007-07-18
The thread is a big help

---

### Post by jn25b on 2007-07-18
I'm running self-hosted, with 2.8.1-Debian-1~dapper1 installed.

Now. When I go to 192.168.0.172/phpmyadmin I get the phpmyadmin entry page.

So where do I go to put myself on the list of approved users?

Cheers

jn25b

---

### Post by Snitz on 2007-07-19
I'm still facing the timestamp issue and I'm not being able to figure it out. I read the topic mentioned here and still no luck. Can anyone help me?

> snitz@Mnets:~$ sudo apt-get install php5
sudo: timestamp too far in the future: Jul 19 10:01:24 2007


---

### Post by Snitz on 2007-07-19
I fixed the problem of the timestamp. However when I tried to download the php5 it said package couldn't be found.

---

### Post by Snitz on 2007-07-19
Permissions to write on my HDD!

I downloaded everything and when I goto [http://localhost/phpmyadmin](http://localhost/phpmyadmin) it asks for a username and password which I have no idea about. So I went to /etc/phpmyadmin/config.inc.php and tried to add a password to the root, and when saving I couldn't save it, it said I don't have a permission to write on this partition. Same thing for my windows partitions who are only accessible. How can I fix this?

---

### Post by treblesix on 2007-07-19
If you have not changed your root password in MySql, then just log in as root with no password.

---

### Post by Snitz on 2007-07-19
> **treblesix said:**
> If you have not changed your root password in MySql, then just log in as root with no password.
I'm trying to login with username: root and no password but it's not working, how can I change the password?
And where can I find the www folder to put my sites in?

---

### Post by Snitz on 2007-07-19
There is something wrong with my phpmyadmin, I uninstalled it and installed it back and still no luck with the password thing, even though I have added a password for the root via terminal by typing this

sudo mysqladmin password <mypass>

still no luck, any suggestions?

---

### Post by ramadhian on 2007-07-19
Currently im tryin to install zCi ([http://zci.sourceforge.net](http://zci.sourceforge.net))

but the application need to activate DBX Extension for PHP..

how to make this work ??

---

### Post by Snitz on 2007-07-19
Please mods, delete this post!

---

### Post by treblesix on 2007-07-19
> **Snitz said:**
> There is something wrong with my phpmyadmin, I uninstalled it and installed it back and still no luck with the password thing, even though I have added a password for the root via terminal by typing this

sudo mysqladmin password <mypass>

still no luck, any suggestions?


As a default Mysql installs with a username of root with no password.

Myphpadmin will log in as root with no password was well.

As for your webpages, they are stored in /var/www/

Ensure you have all you need to install. Look at the install list that was posted at the top of the thread.

---

### Post by Snitz on 2007-07-19
I try to login with root and no password but it keeps redirecting to the login page and after I get in, I keeps logging me out asking me to login. I can't do anything inside phpmyadmin. I tried removing it and installing it again but no luck. :(

---

### Post by treblesix on 2007-07-19
> **Snitz said:**
> I try to login with root and no password but it keeps redirecting to the login page and after I get in, I keeps logging me out asking me to login. I can't do anything inside phpmyadmin. I tried removing it and installing it again but no luck. :(

Uninstall MySql. All the problems you are having is from that i think. Maybe the root password has been changed.

Re-install MYSQL and don't change anything and it will work.

---

### Post by az on 2007-07-19
> **Snitz said:**
> I try to login with root and no password but it keeps redirecting to the login page and after I get in, I keeps logging me out asking me to login. I can't do anything inside phpmyadmin. I tried removing it and installing it again but no luck. :(

See here for the guide to LAMP:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

and to reset a mysql password (reinstalling mysql won't do that...)
[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

---

### Post by michaelp07 on 2007-07-20
I was following the instructions on how to change the MySQL password, because I am having trouble logging in with root and no password. But when using the command:

> /usr/bin/mysqld --skip-grant-tables --user=root

It gives me this error:

> bash: /usr/bin/mysqld: No such file or directory

What do I do?

---

### Post by az on 2007-07-20
> **michaelp07 said:**
> I was following the instructions on how to change the MySQL password, because I am having trouble logging in with root and no password. But when using the command:



It gives me this error:



What do I do?

Are you sure mysql is installed?


dpkg -l |grep mysql

---

### Post by big9er5 on 2007-07-21
hi 
ive got ubuntu, php4 apache2 amd mysql
but cant seem to edit any of the config file of the php.ini file how do i go about doing this it wont let me edit the files and save them in the same location

---

### Post by treblesix on 2007-07-23
can you see your localhost webserver?

[http://localhost](http://localhost)

It should show you the contents of the www folder

---

### Post by ZuLuuuuuu on 2007-08-04
Hi, I installed everything also phpMyAdmin and it works. But only the *root* account can reach the *var/www* directory. Should I switch to *root* user whenever I am developing PHP? Can I use my normal user for developing PHP+MySQL applications? I developed PHP+MySQL applications on Windows but I'm not used to Linux environment about this. Can you explain me what path should I follow for developing PHP?

---

