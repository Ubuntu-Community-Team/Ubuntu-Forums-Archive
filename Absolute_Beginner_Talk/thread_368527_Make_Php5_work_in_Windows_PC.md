---
title: "Make Php5 work in Windows PC"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-02-23
Hello all!

I would like to know how can I fix php5 to work in my windows PC...
I know, I know...
It is Not the greatest place to ask...
But I am at work now...
At home, I use Ubuntu LAMP...

But at work, things can be different...
So, I installed Apache & MySql, and they are looking great!

However, with PHP5 is the problem...
I visited the PHP site & got the Program from there - see here:

[http://www.php.net/get/php-5.2.1-Win32.zip/from/a/mirror](http://www.php.net/get/php-5.2.1-Win32.zip/from/a/mirror)

I then performed the following:

A. I unzipped the folder in "[color=blue]c:\php5[/color]"

B. I edited the file "[color=blue]C:\Program Files\Apache Software Foundation\Apache2.2\conf\httpd.conf[/color]" & added/changed the following:

1. Addind this line "[color=red]# LoadModule php5_module php5apache2.dll[/color]" creates an error & I can't use it...

2. Addind this line "[color=blue]ServerAdmin [email]dvarsam@ubuntu.com[/email][/color]"

3. Then this "[color=blue]ServerName localhost:80[/color]"

4. Then this "[color=blue]DocumentRoot "C:/www"[/color]"
    (I want my Web files to bee here - instead of the Default Folder:
    "C:\Program Files\Apache Software Foundation\Apache2.2\htdocs")

5. Then this: "[color=blue]<Directory "C:/www">[/color]

6. Using this line "[color=blue]DirectoryIndex index.php[/color]" instead of "DirectoryIndex index.html".

7. Adding this line "[color=blue]AddType application/x-httpd-php .php[/color]"

8. Copying & pasting these files from:

    a. [color=blue]C:\php5\php5ts.dll[/color]
    b. [color=blue]C:\php5\php5apache2.dll[/color]
    c. [color=blue]C:\php5\php.ini-recommended[/color]

    into the path "[color=blue]C:\Program Files\Apache Software Foundation\Apache2.2\[/color]"
    When finished, inside the destination path, rename the file "[color=blue]php.ini-recommended" to "php.ini[/color]".

9. Editing the file "[color=blue]php.ini[/color]" inside the destination folder & changing "[color=blue]doc_root =[/color]" to:
    "[color=blue]doc_root = C:\www[/color]"

10. Restarting the apache web server by selecting:
     "[color=blue]Start\All Programs\Apache HTTP Server 2.2.4\Control Apache Server\Restart[/color]"

_Note_:
By restarting the apache server using the above method, you can track any errors occuring...
And in **step B1** above, I get errors if I try to activate it...

The problem is the following:

Whenever I try to access a Web page with "[color=red]php[/color]" code in it, I get a "save as" download window appearing on my screen!!!

How can I fix this?

Thanks.

P.S.1> This has happened to me in the past, when installing LAMP on an Ubuntu PC - but I can't remember what I did to fix this...
P.S.2> I have also performed a search in Yahoo, but many sites suggest using diff approaches & I can't figure out which is the best one...
For this, I used this source site: [http://www.devarticles.com/c/a/Apache/Installing-PHP-under-Windows/4/](http://www.devarticles.com/c/a/Apache/Installing-PHP-under-Windows/4/)

---

### Post by jeduan on 2007-02-25
try to install xampp. [http://www.apachefriends.org/en/xampp-windows.html](http://www.apachefriends.org/en/xampp-windows.html)
It's the easiest way and you don't have to fiddle with config files

---

### Post by dvarsam on 2007-02-25
[QUOTE=jeduan]try to install xampp. [http://www.apachefriends.org/en/xampp-windows.html](http://www.apachefriends.org/en/xampp-windows.html)
It's the easiest way and you don't have to fiddle with config files[/QUOTE]

Thanks for your reply!
Your suggestion worked perfectly!
However, I have the following problem:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/XamppcanNOTshowGreekFontsinWindowsX.jpg[/IMG]

The above text is typed in "[color=blue]Greek[/color]".
Whenever I view this file in my Ubuntu box, the text comes out fine!
(no doubt why [color=red]Ubuntu[/color] is "always" superior compared to Windows... ;))
Greek keyboard layout is already added in my [color=red]Windows XP SP2[/color] machine...
How can I fix this? :-k

Thanks

P.S.> A foreigner viewing the above image would say "it sounds Greek to me!"...
A Greek guy viewing the above image would say "it sounds Chinese to me..."
What do Chinese people say...? :)

---

