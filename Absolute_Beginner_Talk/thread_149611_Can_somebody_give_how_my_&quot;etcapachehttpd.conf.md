---
title: "Can somebody give how my &quot;/etc/apache/httpd.conf&quot; should look like in Ubuntu?"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-24
Hello All!

I am trying to configure my "Apache" & I have to say... it is hard!

The Book I got offers very little help...

Most of its commands & paths given are different that what I have on my Ubuntu...

I would like to know how should my apache's "/etc/apache/httpd.conf" should look if I want it to point to a file "/var/www/test.php".

Right now, the file contains the following:

# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

AddType application/x-httpd-php .php .phtml .html

#


On my book (for Windows) it says the following:

1. Go to the Apache "C:\Program Files\Apache Group\Apache2\conf" & edit 
    "httpd.conf".

    (My path is "/etc/apache/httpd.conf"...)

2. Look for a section that contains a number of LoadModule directives...

    LoadModule userdir_module modules/mod_userdir.so

    (I show above my "httpd.conf" file's contents...)

3. Add the following line to tell apache to load the PHP module on startup:

    LoadModule php5_module c:/php5/apache2.dll

    (What do I need to type-in here? Mine is disabled...)

4. Next, search for the AddType section & add:

    AddType application/x-xttpd-php .php .phtml .html

    (I have added this!)

5. We need to copy php.ini and a DLL file to a system location. Copy from  "C:\php5\" the files  "php.ini" & "php5ts.dll" to the locations "C:\Windows" & "C:\Windows\System" respectively.

    (I am going to start taking drugs man....)

My stupid book, when it comes to installation in contains Linux, Mac OS & Windows...
But when it comes to the part of explaining something - I am left alone in deep waters...)

How can I tell apache on the "/etc/apache/httpd.conf" file to point to the file "/var/www/test.php"?

Visiting "http://httpd.apache.org/docs/2.0/mod/core.html#accessfilename", I got these:

 AccessFileName .acl

 <Directory />
AllowOverride None
</Directory>

What do I do?

Thanks.

---

### Post by dvarsam on 2006-03-24
I tried this:

<VirtualHost 127.0.0.1>
  ServerName [www.test.php](www.test.php)
  DocumentRoot "/var/www/test.php"

      <Directory "/var/www/test.php">
     Order deny,allow
     allow from all
     </Directory>

</VirtualHost>

And I got the following errors:

root@ubuntu:/var/www# /etc/init.d/apache2 restart

 * Forcing reload of web server  (Apache2)... Warning: DocumentRoot [/var/www/test.php] does not exist
Warning: DocumentRoot [/var/www/test.php] does not exist


Honestly I do NOT know what I am doing here...

I just got the above from a site...

I do NOT even know if using "127.0.0.1" is right here...

Thanks.

---

### Post by yanns on 2006-03-24
Be carefull: apache on ubuntu is configured à la debian.

/etc/apache2/httpd.conf contains nothing.
Instead, 

- global configuration is in /etc/apache2/apache2.conf
- virtual host are in /etc/apache2/sites-enabled/*.conf

You should search tutorial, howto on internet.

---

### Post by harisund on 2006-03-24
Are you just trying to get Apache working, and serve PHP files? 

In this case, you don't really need to go about editing any configuration files. 

Also, the Apache2 that comes with Ubuntu when you do apt-get install apache2 is not quite the same as the Apache2 that your book (especially for Windows explains)

The debian version (which Ubuntu uses too) has been extensively modularized. This means there is no longer a single "http.conf" file where you can edit everything you want. Everything is split into multiple files.

---

### Post by dvarsam on 2006-03-25
1. Dear "yanns",

Thank you for your reply!

I guess this was why nothing was working for me... 

My book sucks man!...

Let me try out what you suggested & I will post back!

Thanks again!!!



2. Dear "harisund",

Thank you for your reply!

[QUOTE=harisund]Are you just trying to get Apache working, and serve PHP files? 
[/QUOTE]

Yes.
I have already managed to fix this!
And I have managed to post my Web Site out there...
But people see a directory with folders & NOT my actual web page...
So, I think I needed to edit that "/etc/apache/httpd.conf", which turned out to be some other file in the Ubuntu system...
Please give me some time to play around with your "new" feedback & I will write back...

[QUOTE=harisund]
The Apache2 that comes with Ubuntu when you do apt-get install apache2 is not quite the same as the Apache2 that your book (especially for Windows explains).
[/QUOTE]

I know, my book sucks! $&(*%&*$#$@
But I do NOT think I would find much about Ubuntu or debian in Greece...

[QUOTE=harisund]
The debian version (which Ubuntu uses too) has been extensively modularized. This means there is no longer a single "http.conf" file where you can edit everything you want. Everything is split into multiple files.[/QUOTE]

Multiple Files???????

That sucks!!!!!

Oh my God.......!!!

That means, I will have to perform a lot of "voodoo" to make this work.......

How many files is it NOW separated to?
Probably 3?,
Maybe 5? lol

I hope I can live through it....

And what are the new "config" file names, the ones I might have to work with?

Thanks!!!

P.S.> I hope, I can survive through this....man....
         In the end, if I succeed, I will throw an Ubuntu Party....hehe
         And you are ALL invited! 
        Shampagne is going to be with compliments (i.e. free!)

---

### Post by harisund on 2006-03-25
I am going to assume you simply did an
apt-get install apache2 php5

From this point on, everyfile I mention is in /etc/apache2

Wait, did you go to the /etc/apache2 folder? Did you find a file called README? Hmm..did you read it? 

(.)apache2.conf
This has most configuration settings. You can read through it. Very well commented. Typically if you are the only user, you might want to change the
User <your user name>
Group <your user name> 

Trust me, this file is beautifully commented. Has everything you need. If you don't understand something, leave it ! (unless of course, you want to learn about it.) 

Around 400 lines, I believe. 

(.) sites-available/default
In this file, you can change the default directory from which to serve files. So if you want this to be your home folder, you would have /home/<user_name>

You can follow the syntax for creating alias pages as well. 

Have fun !

---

### Post by dvarsam on 2006-03-26
Dear "harisund",

Thanks for your reply!!!

Also, sorry for my late reply, but in my Country it was already late at night, and a man's got to sleep...

[QUOTE=harisund]
I am going to assume you simply did an "apt-get install apache2 php5"
[/QUOTE]

Yes, that is how I installed it!

[QUOTE=harisund]
Wait, did you go to the /etc/apache2 folder? Did you find a file called README? Hmm..did you read it? 
[/QUOTE]

If I do not even know what the path or destination folder is, how am I supposed to know what to look for to read?.........
In addition, my book "SAMS Teach Yourself PHP, MySQL & Apache" did NOT mention a README file...
... And it is SUPPOSED to provide the way to do it in Windows, Macintosh & Linux...
... And that was WHY I bought this thing for...
... My man, this book is sending me straight to the guillotine...
... What kind of book does NOT mention a good README file man....?
Book = @#$^&()*$$%#
At the same time, in the Internet, "Ubuntu" is considered the BEST (in rank) Linux distribution...
IF the book wanted to provide a "HowTo" for Linux, shoudn't it have included the "HowTo" for the most popular distribution in the Linux world?????
And, "assuming" they did, why are ALL the paths different?

[/QUOTE]
(.)apache2.conf
This has most configuration settings. You can read through it. Very well commented. Typically if you are the only user, you might want to change the
User <your user name>
Group <your user name> 
[/QUOTE]

Yes, you guessed right, I am the only user on this Ubuntu!
My man, ALL your guesses about my system are ALL correct?
Are you a "mind" reader man?
You could make some money out of this...!!!
A "psychic ubuntu line" perhaps...
A "don't tell us your problems cauz we allready know them"...
And these guys make a lot of money man...
 
[/QUOTE]
(.) sites-available/default
In this file, you can change the default directory from which to serve files. So if you want this to be your home folder, you would have /home/<user_name>
You can follow the syntax for creating alias pages as well. 
[/QUOTE]

Yes, I really need to know, how to do this!!!
In the past, I managed to open my Port 80 sucessfully (it is still open as I speak), made my "/var/www" folder Publicly available, but ALL the visitors did NOT actually see a Web Page, but a Directory with some folders & files in it...

So, in some way, SOMEWHERE inside the "apache2.conf" file (you suggested), there must be a line (hopefully!) for the name of the file my site should point to, ...to open....?
Because, ALL the people in the Internet, are viewing a Directory & NOT an actual Web Page (with text)...

I will now go & read what you suggested man,

Thanks!

---

### Post by harisund on 2006-03-26
[QUOTE=dvarsam]Dear "harisund",

Thanks for your reply!!!

Also, sorry for my late reply, but in my Country it was already late at night, and a man's got to sleep...
[/QUOTE]

Sure !

> Yes, that is how I installed it!
Good. That is the best way to do so. I was afraid you compiled from source or something. 

> In addition, my book "SAMS Teach Yourself PHP, MySQL & Apache" did NOT mention a README file...
... And it is SUPPOSED to provide the way to do it in Windows, Macintosh & Linux...
... And that was WHY I bought this thing for...
... My man, this book is sending me straight to the guillotine...
... What kind of book does NOT mention a good README file man....?
Book = @#$^&()*$$%#
At the same time, in the Internet, "Ubuntu" is considered the BEST (in rank) Linux distribution...
IF the book wanted to provide a "HowTo" for Linux, shoudn't it have included the "HowTo" for the most popular distribution in the Linux world?????
And, "assuming" they did, why are ALL the paths different?

Ok ok ok relax..let's see. that book is probably quite a few years old.. and considering Ubuntu's first version was in 2004 .. hmm.. I wouldn't expect them to have Ubuntu specific information. 

> Yes, you guessed right, I am the only user on this Ubuntu!
Hmm..most home users are.. So you will need to change the User and Group part in the apache2.conf. Get it? 
> My man, ALL your guesses about my system are ALL correct?
Are you a "mind" reader man?

Well.. I was just explaining the default settings. Besides that is quite the advantage with these forums. If you see to my left, I have around 280 posts. And the first few ones, they were all on the apache questions of course. Do you think I found a manual for configuring apache2 on ubuntu? Nope ! I just found people like myself willing to help me out, and so here I am returning a favor !
> You could make some money out of this...!!!
hmm.. a nice line of thought.. but wait, aren't we in an open source world??

> 
In the past, I managed to open my Port 80 sucessfully (it is still open as I speak), made my "/var/www" folder Publicly available, but ALL the visitors did NOT actually see a Web Page, but a Directory with some folders & files in it...

Actually, by default Apache is configured by default to deliver a file called index.html or index.htm or index.php. If it doesn't find any, it will simply list the contents of the directory. 

Now, for some reason, in Ubuntu, /var/www doesn't have a index.html page, and consequently all you see is a directory (the /var/www directory.) If you want, go ahead create a HTML page, name it index.html and use your browser to access your machine. You will see the page you made !!!

> So, in some way, SOMEWHERE inside the "apache2.conf" file (you suggested), there must be a line (hopefully!) for the name of the file my site should point to, ...to open....?
Nope ! In ubuntu, go to /etc/apache2/sites-available. Open the file called default (as sudo or root of course)

Now, this is the folder that decides on the pages you want to see.. 

If you look around, you will find /var/www under 2 places, one next to DocumentRoot and one inside <Directory /var/www/>. Change both. For example, in my machine I have. 
```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/harisund/
	<Directory />
		Options FollowSymLinks
		AllowOverride all
	</Directory>
	<Directory /home/harisund/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride all
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

```

There are a ton of other features, such as whom to allow to view the pages, whether or not the directory should be shown and so on... 
> Because, ALL the people in the Internet, are viewing a Directory & NOT an actual Web Page (with text)...
Not any more they won't !

> I will now go & read what you suggested man,
Yes, the official term for that is RTFM .. google that and check out what that means !

---

### Post by dvarsam on 2006-03-27
Dear "harisund",

You have been of great help!!!

You have helped me understand a lot!!!

But still there are a couple of questions I have...


> **harisund]
you will need to change the User and Group part in the apache2.conf. Get it? 
[/QUOTE]

So, lets say I change the default:

User www-data
Group  www-data

To:

User dimitris
Group dimitris

_Question 1_:
If from my Ubuntu meny, I:

1. click on "Applications\System Tools\MySQL Administrator"
2. On the window that opens up, I type in:
    a. Under "Server Hostname", I type "localhost"
    b. Under "Username", I type "root"
    c. Under "Password", I do NOT type anything (since I have not yet created any)

How does this "root" username (under 2.b), relate to the lines we changed to the "apache2.conf" file (e.g.: User dimitris & Group dimitris)?

In the End, I am going to end up with 2 users?
a. Dimitris
b. root

And why would I want to do that?


[QUOTE=harisund]
By default Apache is configured by default to deliver a file called index.html or index.htm or index.php. If it doesn't find any, it will simply list the contents of the directory. 
Now, for some reason, in Ubuntu, /var/www does NOT have a index.html page, and consequently all you see is a directory (the /var/www directory).
If you want, go ahead create a HTML page, name it index.html and use your browser to access your machine. You will see the page you made !!!
[/QUOTE]

Now, here I have a BIG problem.
From my experience, Apache can NOT show ".html" code...

_For example_:

I create a STATIC "index.html" file with contents:

Text

I put it inside the "/var/www" folder & NO problem, I can see the file by doing an "htttp://localhost/index.html" on the Mozilla Firefox.

I then create a NON STATIC "index.html" file with contents:

<html>
    <head>
          <title>PHP Test</title>
    </head>

    <body>
          <?php echo '<p>Hello World</p>' said:**
> 
There are a ton of other features, such as whom to allow to view the pages, whether or not the directory should be shown and so on... 
Not any more they won't !


It is quite relieving, that if I add a file named "index.html" to the directory named "/var/www", that the directory will NOT show in Public...

And I say "relieving", because Ubuntu also includes inside the "/var/www" directory the file "phpmyadmin"...
AND this could mean that any outsider IF he had access to ALL the directory's contents, he could hack into my MySQL from the "phpmyadmin" File...

I know that this would be difficult, but it COULD happen...


Thank you for all your help!

I owe you one...man!

P.S.> Sorry for the late reply, but if you noticed at this Forum, I had problems with my Ubuntu's monitor's Resolution...
Thank God I fixed that, and came back to this Thread...

---

### Post by harisund on 2006-03-27
> **dvarsam]
So, lets say I change the default:

User www-data
Group  www-data

To:

User dimitris
Group dimitris
[/QUOTE]
Yes, that's what I had in mind too. 

> 
_Question 1_:
If from my Ubuntu meny, I:

1. click on "Applications\System Tools\MySQL Administrator"
2. On the window that opens up, I type in:
    a. Under "Server Hostname", I type "localhost"
    b. Under "Username", I type "root"
    c. Under "Password", I do NOT type anything (since I have not yet created any)

How does this "root" username (under 2.b), relate to the lines we changed to the "apache2.conf" file (e.g.: User dimitris & Group dimitris)?

In the End, I am going to end up with 2 users?
a. Dimitris
b. root

And why would I want to do that?

Hmm... let's go over a couple of things here. 

Firstly, Ubuntu doesn't create a root user. So you have no user called root (unless you wish to create one.) Everything you do is through dimitris using the sudo command. 

Secondly, our mySql pal wants a user named "root". Trust me, that "root" has nothing to do with Ubuntu's (or in general any Unix's) root user. (Yeah, I know. I found it the hard way too) The "root" for mySql is merely the user who can access and change mySql databases. There is a mySql command for changing the root password. Again, a quick internet search reveals
```
mysqladmin -u root password <your_pass>
```
should change the password, which is what you would use when using the mySql administrator thing. 

On a side note, I do not have a handy ubuntu machine with me immediately. I will have one shortly and after that I will start playing around with MySql and let you know more. 

> 
Now, here I have a BIG problem.
From my experience, Apache can NOT show ".html" code...

_For example_:

I create a STATIC "index.html" file with contents:

Text

I put it inside the "/var/www" folder & NO problem, I can see the file by doing an "htttp://localhost/index.html" on the Mozilla Firefox.

Actually, if its labelled index.html, you wouldn't even need to go to [http://localhost/index.html](http://localhost/index.html). You can simply go to [http://localhost](http://localhost) and still you will get that file only. 

> 
I then create a NON STATIC "index.html" file with contents:

<html>
    <head>
          <title>PHP Test</title>
    </head>

    <body>
          <?php echo '<p>Hello World</p>' said:**
> 
Yes, you will only be seeing what you typed. 
[quote]
I do NOT know if I am using the correct Terminology here, but it seems as if the "interpretation" engine does NOT "interpret" the code...
OR is it called "parsing" the code...?
Again, NOT sure about the correct Terminology, but it is as if, some TAGS can NOT be translated...

Hmm.. that's the way php is supposed to work. If you are having php code, you should tell Apache that it should call upon the services provided by our PHP parser. Consequently, only files ending with a .php can be used to write php code in. 
[quote]
And ".php" files are interpreted correctly (NO problem there)!!!
Only with ".html" files I have the problem...

Yep. That's the way it's supposed to work. For example if you look at the very ubuntuforums default home page, it would be [http://ubuntuforums.org/index.php](http://ubuntuforums.org/index.php)

> 
And inside the "apache2.conf" file, I have replaced the line:

# AddType application/x-httpd-php .php

With:

AddType application/x-httpd-php .php .phtml .html

Surprising. I didn't do that. And when I looked at the apache2.conf in my machine it is commented out. So I would suggest commenting it out, unless of course you know what you are doing. 
> 
Then I have restarted the "apache" server with:

/etc/init.d/apache2 restart

But I still get the same problem....???

yeah.. that's the way php is supposed to work. It's like asking gcc to compile a valid c code in a file that doesn't end with .c 

> 
_Question 2_:
What is the problem with handling ".html" files?
How can I fix this?

Meaning? I am sorry I didn't get you on this one.. 

> 
It is quite relieving, that if I add a file named "index.html" to the directory named "/var/www", that the directory will NOT show in Public...

And I say "relieving", because Ubuntu also includes inside the "/var/www" directory the file "phpmyadmin"...
AND this could mean that any outsider IF he had access to ALL the directory's contents, he could hack into my MySQL from the "phpmyadmin" File...

I know that this would be difficult, but it COULD happen...

Hmm.. ok give me the address of your machine.. I will try it, pwn your machine and let you know how things are going.. 

hehe.. just kidding.. don't worry. Besides, you meant "crack" in place of "hack" right? 

> 
P.S.> Sorry for the late reply, but if you noticed at this Forum, I had problems with my Ubuntu's monitor's Resolution...
Thank God I fixed that, and came back to this Thread...
Glad you could fix that. I haven't yet delved into X.org hacking yet.. not that I have any intention of doing it yet ..

Also, my name is Hari. I go by my id harisund everywhere because that's the first user name my dad created for me when I was around 3 (I started using it when I was 14 though..). My full name is Hari Sundararajan, and my dad used the first four letters of my first name (which is the whole name) and the first four letters of my last name.

---

### Post by dvarsam on 2006-03-27
Dear hari,

                thanks for your reply!


[QUOTE=harisund]

So, lets say I change the default:

User www-data
Group www-data

To:

User dimitris
Group dimitris

Yes, that's what I had in mind too. 
[/QUOTE]

Ok, I understood what "root" is & why MySQL needs it!

But why don't I create a:

User root
Group root

Instead of:

User dimitris
Group dimitris

What is the reason we are really creating this?

The user "dimitris" is a guy able ONLY to view the databases?
What is his role in this game (meaning MySQL)?
Why are we declaring this guy, for what purpose?


[QUOTE=harisund]
Hmm.. that's the way php is supposed to work.
If you are having php code, you should tell Apache that it should call upon the services provided by our PHP parser.
Consequently, only files ending with a .php can be used to write php code in. 
[/QUOTE]

So, I can NOT mix code (PHP & HTML) into a single file?
Because, in some Online Tutorials, they seem to mix stuff...

Take a look here for example:

[url]http://gr.php.net/manual/en/tutorial.firstpage.php[url]

And the above link comes STRAIGHT from the PHP Home site!!!

How is it possilbe that they are mixing ".php" & ".html" code on the SAME file?

And it is their FIRST example listed there... the EASIEST there......?

[QUOTE=harisund]
What is the problem with handling ".html" files?
How can I fix this?

Meaning? I am sorry I didn't get you on this one.. 
[/QUOTE]

I meant, it could be understandable that ".html" & ".php" files could both exist & work with each other, as long as they are NOT both contained in the SAME file together...
But the site I am suggesting you to visit is contradicting...

> Also, my name is Hari.

I bet, by now, you know my name too! (does dimitris remind you of anything...?)

Thanks.

---

### Post by dvarsam on 2006-03-27
> 

And inside the "apache2.conf" file, I have replaced the line:

# AddType application/x-httpd-php .php

With:

AddType application/x-httpd-php .php .phtml .html

Surprising. I didn't do that. And when I looked at the apache2.conf in my machine it is commented out. So I would suggest commenting it out, unless of course you know what you are doing.


According the to the "SAMS Teach Yourself" Book that I have here in front of me, and in page 70, it says the following:

> 
Integrating PHP with Apache on Linux/Unix:

To ensure PHP & Apache get along, you need to check for/add a few items to the "httpd.conf" configuration file.
First look for a line like the following:

LoadModule php5_module  modules/libphp5.so

If this line is NOT present or appears with a pound sign (#), at the beginning of the line, you must add the line or remove the #.

This line tells Apache to use the PHP shared object file that was created by PHP build process (libphp5.so).

Next, look for this section:

# AddType allows you to add to or override the MIME configuration
# file mime.types for specific file types.

Add the following line:

AddType application/x-httpd-php .php .phtml .html

This ensures that the PHP engine will parse files that end with the .php, .phtml and .html extensions. Your selection of filenames might differ.

Save the File & Restart Apache. When you look in your error_log you should see something like the following line:

[Sun Sep 2604 10:42:47 2004] [notice] Apache/2.0.52 (Unix) PHP/5.0.2 configured

PHP is now part of the Apache Web Server.


So, my problem is the following:

If I have added the line:

AddType application/x-httpd-php .php .phtml .html

NOT in "httpd.conf" but in "apache2.conf", why can't Apache parse my ".html" files?
(I added it to "apache2.conf" because in there there are 3 lines that start with "AddType" & one of them is "AddType application/x-httpd-php .php". So it MUST be now in "apache2.conf" & NOT in "httpd.conf"...)

I can NOT figure it out...

I have installed from the Terminal the following "packages" & in the order displayed below:

1. apt-get install mysql-server-4.1
2. apt-get install apache2
3. apt-get install php5
4. apt-get install libapache2-mod-auth-mysql
5. apt-get install php5-mysql
6. apt-get install phpmyadmin
7. apt-get install mysql-admin

Is there some package or library I am missing & it could be the reason why ".html" type files do not "parse"?
Even though I tell PHP to parse them, it does NOT...

AND the line:

LoadModule php5_module  modules/libphp5.so

should be lying inside the "apache2.conf" file or inside the "httpd.conf" file?

Please help guys...

There must be somebody out there that has made it work on his Ubuntu...

I will try out anything, just tell me what you want me to do...

Format?
Cut it in pieces?
Attack?
Demolish?
Observe?
Kill?
Destroy?
Tickle it?
.............

Thanks.

P.S.> This st*pid "uncle SAMS" book has destroyed me man... There is not even one command that is appropriate for my Ubuntu....](*,)

---

