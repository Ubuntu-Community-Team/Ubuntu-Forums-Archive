---
title: "Formatted my HD - Reinstalled Ubuntu 5.10 Desktop &amp; want Help to Config PHP &amp; Apache"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-29
Hello ALL!!!

This is the SECOND time I am attempting to Try to make PHP & Apache work out with My Ubuntu...

I am PHYSICALLY exhausted!!!

I am tired, FEELING hopeless & thinking to go back to Windows...

I have tried so hard to learn Ubuntu, and every time, I get myself into more & more troubles...

Lately, I have dedicated ALL my Personal time & Work time, and have managed to achieve VERY little...

I need to create THE SIMPLEST PHP & HTML Web Page possible so that I can get myself running in the PHP programming world...

I have invested a lot in my Ubuntu (money wise & hope wise)....

I have visited the following wiki:
[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

I have bought a BOOK,

AND have read many (this & other) Forum's Posts!!!

(the only thing I have NOT done yet is give somebody a "blow*ob" to give me a solution on how to make things work out...)


I _NEED_ your HELP in this...

I Formatted my Hard Drive, to have the Cleanest (possible) Ubuntu 5.10 _Desktop_ (not Server) install, and performed the following:


_Part A_:
I installed the following Packages:

01. apt-get install build-essential
02. apt-get install mysql-server-4.1
03. apt-get install apache2
04. apt-get install php5
05. apt-get install libapache2-mod-auth-mysql
06. apt-get install php5-mysql
07. apt-get install phpmyadmin
08. apt-get install mysql-admin
09. apt-get install php4-cgi
10. apt-get install php5-cgi

Note:
I did NOT install "libapache2-mod-php5", because it gets automatically installed by default when installing "php5".


_Part B_:
I then typed the following:

1. mysql_install_db
2. mysqladmin status    (To test that MySQL is running)

    Note:
    I did NOT type "mysqld_safe &" because the MySQL Server starts automatically 
    after the installation of "MySQL".

3. a2enmod actions
4. a2enmod ssl
5. a2enmod rewrite
6. a2enmod suexec
7. a2enmod include 

    Note:
    The above "Modules" were found installed, and I got the following message:
    "To enable, run "/etc/init.d/apache2 force-reload".

8. /etc/init.d/apache2 force-reload   (to restart the "apache" Web server)


_Part C_:
I edited the following files (according to the Ubuntu wiki):

1. "/etc/apache2/apache2.conf"

    a. I replaced:

        User www-data
        Group www-data

        with:

        User dimitris
        Group dimitris

    b. I replaced:

        AddType application/x-httpd-php .php

        with:

        AddType application/x-httpd-php .php .phtml .html


2. "/etc/php5/apache2/php5.ini"

    a. I replaced:

        ;  extension=msql.so

        with:

        extension=msql.so


_Part D_:
I then Restarted the "apache" Web Server to APPLY the new changes, by typing:

1. "/etc/init.d/apache2 force-reload"  (I had also performed a reload previously...)


_Part E_:
I then performed these important steps before testing:

1. I created a simple page, by performing the following steps:

    a. From the Menu, I selected "Applications\Accessories\Text Editor"
    b. I typed in "<?php phpinfo(); ?>"
    c. From the Menu I selected "File\Save As":

        1. Under "Name", I typed "simple.php"
        2. Under "Save in folder", I selected: "Desktop"
        3. Under "Character Coding", I selected: "Current Locale (UTF-8)"
        4. Then, I clicked on the button named "Save"

2. I moved the page I created, to the Web Page Directory, by typing:

    mv /home/dimitris/Desktop/simple.php /var/www/simple.php

3. I launched the Mozilla Firefox Internet Browser & performed the following:

    a. From the Menu, I selected "Edit\Preferences"
    b. From the left, I selected the "Privacy" section
    c. On the right, under "Cookies", I clicked on the button named "Clear"
    d. On the right, under "Cache", I clicked on the button named "Clear"
    e. Then I clicked on the button named "OK"


_Part F_:
This is the moment of Truth!
To TEST whether my Web Page is working:

1. I launched a Mozilla Firefox Web Browser window & typed:

        [http://localhost/simple.php](http://localhost/simple.php)

    ONLY to get the following:

    A window comes up with title name:

        "Opening simple.php"

    AND contents:

        You have chosen to open
        simple.php
        which is a: PHP script
        from: [http://localhost](http://localhost)

        What should Firefox do with this file?

        Open with: a. gedit (default)
                           b. Other...

        Save to Disk.

        [ ]Checkbox: Do this automatically for files like this from now on.

    AND buttons: "Cancel" & "OK"


_Result_:
I guess this "Part F" section stands for "Dimitris (me), you F*CKED UP!!!"
OR: You FAILED TOTALLY!!!

_Question_:
CAN Someone explain to me WHAT DID I DO WRONG HERE?

PLEASE guys, I am running crazy here...

I want to be able to VIEW ".php" & ".html" Web Pages...

I told you in THE MOST POSSIBLE DETAIL what I did...

Try it out yourselves & TELL me if it works for you in the Ubuntu 5.10 Breezy DESKTOP (not Server) install...

HOW can I fix this...???

PLEASE HELP!!!!!!!
????????????????

Thanks.

---

### Post by dvarsam on 2006-03-29
Sorry, but if your write:

Current Locale ( UTF- 8 )

without any space between the "8" & ")" you get a 8).

---

### Post by mlind on 2006-03-29
looks like apache doesn't know how to serve .php file?

I don't know why you need to edit /etc/apache2/apache2.conf
if you've got php5 module enabled then you should view /etc/apache2/mods-enabled/php5.conf

But I never had to edit any configuration files to get php5 working..

What if you enable userdir module and try to access .php file locally?

---

### Post by dvarsam on 2006-03-29
[QUOTE=mlind]looks like apache doesn't know how to serve .php file?

I don't know why you need to edit /etc/apache2/apache2.conf
if you've got php5 module enabled then you should view /etc/apache2/mods-enabled/php5.conf

But I never had to edit any configuration files to get php5 working..

What if you enable userdir module and try to access .php file locally?[/QUOTE]

How do I do that?

P.S. 1> I just edited the files according to the Wiki I supplied...

P.S. 2> In the meantime I will try to UNDO ALL the changes & try out what you suggested with NO changes...

---

### Post by dvarsam on 2006-03-29
I performed an UNDO & nothing worked...

[QUOTE=mlind]
if you've got php5 module enabled
[/QUOTE]

How can I re-enable the php5 module?

What do I type in the Terminal?

I do NOT know how to do that...

---

### Post by mlind on 2006-03-29
[QUOTE=dvarsam]How do I do that?

P.S. 1> I just edited the files according to the Wiki I supplied...

P.S. 2> In the meantime I will try to UNDO ALL the changes & try out what you suggested with NO changes...[/QUOTE]

Ok, I don't know what the wiki suggests, but here's how I've done it couple of times with Breezy and Dapper.

using apt-get
* install php5 and apache2 meta-packages (with dependencies)
* install mysql and php5-mysql extension (usually I use postgresql)

* enable userdir module by doing *sudo a2enmod userdir*
* create public_html on my home forder by doing *mkdir ~/public_html*
* start apache if it's not already running by doing *sudo /etc/init.d/apache2 start*

* create simple php testfile, for example ~/public_html/testfile.php, containing
only 

```

<?php phpinfo(); ?>

```

* open browser and access [http://localhost/~mlind/testfile.php](http://localhost/~mlind/testfile.php)

---

### Post by dvarsam on 2006-03-29
> **mlind]

using apt-get
* install php5 and apache2 meta-packages (with dependencies)
* install mysql and php5-mysql extension (usually I use postgresql)
[/QUOTE]

I opened Synaptic Package Manager & searched for a:

php5-meta
apache2-meta

And got nothing!
Do these packages have a name?


[QUOTE=mlind]
* enable userdir module by doing *sudo a2enmod userdir*
* create public_html on my home forder by doing *mkdir ~/public_html*
[/QUOTE]

I am not so fond of changing too many things now...
I would prefer to stick to the "/var/www" directory.

[QUOTE=mlind]
* start apache if it's not already running by doing *sudo /etc/init.d/apache2 start*
[/QUOTE]

I always use that command.

[QUOTE=mlind]
* create simple php testfile, for example ~/public_html/testfile.php, containing
only 
```

<?php phpinfo() said:**
> 

That is what I did & NOT even that works.
You see, before I formatted my Ubuntu, it worked OK - only HTML did NOT work.
Now with the NEW format, nothing works!!! 

[QUOTE=mlind]
* open browser and access [http://localhost/~mlind/testfile.php](http://localhost/~mlind/testfile.php)


As I said before, again, I prefer to stick to the "/var/www" folder.

Thanks.

---

### Post by siminone on 2006-03-29
Hi dvarsam, I got Apache up and running with no fuss using the following qucksteps (starting from step 24). This uses PHP4.

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

I'm not sure if you want to uninstall apache and PHP or do a clean install of Ubuntu before you start the above steps.

Last words, it is basic and does not deal with secutiry  but it does get apache up and running with PHP and mysql :-)

---

### Post by dvarsam on 2006-03-29
[QUOTE=siminone]Hi dvarsam, I got Apache up and running with no fuss using the following qucksteps (starting from step 24). This uses PHP4.

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

I'm not sure if you want to uninstall apache and PHP or do a clean install of Ubuntu before you start the above steps.

Last words, it is basic and does not deal with secutiry  but it does get apache up and running with PHP and mysql :-)[/QUOTE]

Thanks for your reply!!!

I will try it out!

For some reason, it has passed through my mind that it could be a problem, with php5...
And I have thought of using php4 instead...
So, it is good you are suggesting using it!
I will visit, try it out & post back!

Thanks.

P.S.> Currently, the way things are with me..., I am NOT concerned with security...

---

### Post by siminone on 2006-03-29
no probs dvarsam but I don't think it has to do with PHP5. 

The howto is nice and easy and gets it up and running, it does not mean it is secure !!

For info, I use a 'sandpit' to muck about with PHP. This is useful as I don't have the hassle of having to 'sudo' every time to update the files and I can create sub-folders which apache recognises.

if you edit the file (or create it) /etc/apache2/conf.d/alias

Alias /sandpit /media/userarea/apache/
<Directory /media/userarea/apache/>
  Options +Indexes
</Directory>
 
You access this 'sandpit' [http://localhost/sandpit/](http://localhost/sandpit/)

---

### Post by mlind on 2006-03-29
[QUOTE=dvarsam]I opened Synaptic Package Manager & searched for a:

php5-meta
apache2-meta

And got nothing!
Do these packages have a name?
[/QUOTE]

yes, php5 and apache2.



[QUOTE=dvarsam]
I am not so fond of changing too many things now...
I would prefer to stick to the "/var/www" directory.
[/QUOTE]

well if you understand what userdir is trying to accomplish, you see that
you actually change less things and break less things. /var/www may
require root permissions, home folders doesn't.

you should review any apache server's logs on /var/log/. they usually show
what's wrong on your setup.

---

### Post by schmidty on 2006-04-20
This might seem like a stupid answer but I was having the same problem with php5 and Apache2. I simply reinstalled php5 and cleared my cache in Firefox and all worked fine!

Try clearing the cache in your web browser.

Schmidty

---

### Post by aegypius on 2006-05-26
I think i have the same problem. I install php, mysql, phpmyadmin, apache2 and every think work fine (I think) but when i trie to open php file nothing append in the browser, but open the file in gedit. With html files work ok. 

The day a install apache2, etc, i open phpmyadmin and works fine, but 1 day after nothink work.

I read a lot of posts and i can't find solutions. 

(sory my english):mrgreen:

---

