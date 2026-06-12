---
title: "Apache php5 problems"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by macmichael01 on 2006-06-03
ok, I need the gd() lib installed or enabled with php and so I just decided to upgrade apache2 php4 to apache2 php5 assuming that gd will be enabled. the problem that I am having is when I access my url it tries to download a  .phtml extension.  There shouldn't be anything wrong with the mime times and I dont even have a .phtml file in my home directory. I also tried test.php and it wants me to download. what is going on I just want a freakin web server. I have tried all of the commands for installing and upgrading listed on this site. what now? also Xampps looked very pleasing but being the new person that I am to linux I can get the damn gzip file to extract to the opt directory that it explains in the installation giude. I use firefox to download zip to my desktop. then start up a comannd window and type the following:   tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt and it crapps out an error saying unknown id. I dont know what the heck im doing wrong!!

---

### Post by ChrisNTR on 2006-06-03
In your httpd.conf file ( in /etc/apache2/) try adding the line;

```
 LoadModule php5_module /usr/lib/apache2/modules/libphp5.so 
```

Make sure you have libapache2-mod-php5 installed via Synaptic Package Manager.

Then run sudo /etc/init.d/apache2 restart

and try the .php file again - That should work :) Hope it helps.

This should fix the whole downloading the .php file, not sure about the rest.

---

### Post by macmichael01 on 2006-06-03
OK i tried to reinstall the lib and I get this message:

libapache2-mod-php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

I added the line in the conf file and restarted  it works when I goto: [www.myurl.com/test.php](www.myurl.com/test.php)

but it's not recongizing index.php as the default for when I just tyoe my url [www.myurl.com](www.myurl.com)  do i need to specify somewhere. I thought that I already did

---

### Post by ChrisNTR on 2006-06-03
[QUOTE=macmichael01]OK i tried to reinstall the lib and I get this message:

libapache2-mod-php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

I added the line in the conf file and restarted  it works when I goto: [www.myurl.com/test.php](www.myurl.com/test.php)

but it's not recongizing index.php as the default for when I just tyoe my url [www.myurl.com](www.myurl.com)  do i need to specify somewhere. I thought that I already did[/QUOTE]

Try looking at this site - [http://help.hardhathosting.com/question.php/114](http://help.hardhathosting.com/question.php/114)

Might help you out.

---

### Post by justfred on 2006-06-03
Hey , I ran ito similar problems.

[history] I seem to broken my apache2 php5 config when trying to look if I could have only the php4 modules and not php5 as php5 seems to break acid-mysql. However it seems it is not possible using the synaptic packet manager to this properly.  So I tried to revert all the changes I did and found that now I could not serve php files anylonger with apache2 : a dialogbox appears asking to save a PHTML file.

[now] so after numerous trials to completely remove apache2 and php related files and reinstall using 

sudo apt-get install apache2 php5

and I did have to uncomment the php related lines in apache2.conf as well as to make the links to php5.conf and php.load in /etc/apache2/mods-enabled/.

The situation is now like :
[http://localhost](http://localhost)    will still ask to download a PHTML type of file

but

 [http://192.168.0.1](http://192.168.0.1)  will correctly display the result of phpinfo() in the index.php

The strange thing is that I am quite sure the [http://localhost](http://localhost) did work correctly before.

Any ideas ?

PS I am rather new to Ubuntu and linux

---

### Post by macmichael01 on 2006-06-03
thanks for your help.  The directory indexing is already in the conf file and I have index.php specified as the file to look for. well I will keep messing around with it. It will eventually work.  thanks!!

---

### Post by uglysmurf on 2006-06-04
I'm experiencing similar problems, and I don't remember doing anything special for this to work in Breezy.  

1.  installed apache2 and php5, and added my old php content to /var/www.
2.  accessing via [http://127.0.0.1/test.php](http://127.0.0.1/test.php) WORKS
3.  accessing via [http://localhost/test.php](http://localhost/test.php) WORKS
4.  accessing via [http://192.168.1.100/test.php](http://192.168.1.100/test.php) WORKS
5.  accessing via [http://mybox/test.php](http://mybox/test.php) WORKS
6.  accessing via [http://myurl.com/test.php](http://myurl.com/test.php) FAILS

And by FAILS, I mean it will ask me to download a phtml file.  Oddly, accessing via [http://myurl.com/test.php](http://myurl.com/test.php) from anywhere else but the box I'm hosting from works, it's only when accessing from my own box that it fails.

Anyone have any ideas what this is an indication of?

[EDIT] I saw in another [thread]("http://ubuntuforums.org/showthread.php?t=128777") a [post]("http://ubuntuforums.org/showpost.php?p=726604&postcount=3") from [ZylGadis]("http://ubuntuforums.org/member.php?u=56653") that recommended clearing the browser cache for this symptom, and suprise suprise, it worked!

---

### Post by adamkane on 2006-06-07
Install this way:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

