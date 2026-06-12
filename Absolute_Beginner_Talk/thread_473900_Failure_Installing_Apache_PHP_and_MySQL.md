---
title: "Failure Installing Apache PHP and MySQL"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by jorgepedret on 2007-06-14
I've been trying to install this three packages during 2 days by now! I have followed every tutorial I've seen and none of them seem to work.

I tryed with synaptic, throug the console (apt-get), even downloading the source packages from the internet and compiling each of them. And nothing works.

After I try installing apache, I go to the browser and type [http://localhost](http://localhost) and it says 

Unable to connect
Firefox can't establish a connection to the server at localhost.

I have done this before (not many times, but I've done it) and it worked, I dont know whats happening now...

Can somebody give me a hand with this?

---

### Post by az on 2007-06-14
> **jorgepedret said:**
> I've been trying to install this three packages during 2 days by now! I have followed every tutorial I've seen and none of them seem to work.

I tryed with synaptic, throug the console (apt-get), even downloading the source packages from the internet and compiling each of them. And nothing works.

After I try installing apache, I go to the browser and type [http://localhost](http://localhost) and it says 

Unable to connect
Firefox can't establish a connection to the server at localhost.

I have done this before (not many times, but I've done it) and it worked, I dont know whats happening now...

Can somebody give me a hand with this?

I would sugges this and only this:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Is something else using port 80?  Skype ties up your port 80, so you can't run apache.

---

### Post by jorgepedret on 2007-06-14
I closed skype suspecting that it could be its fault, but still doesnt work.

I removed everything and started from cero. I went to synaptic and Edit->Mark Packages By Task 
and selected LAMP server, which installs all the packages that I need. And now It seems that is the php that is not working, because when I do [http://localhost](http://localhost) it attemps to download a phtml file (with a random string name, that doesnt exist on my server root) and it contains the source code of the file that its supoused to be there.

For example in my server root I have a file called index.php when I go to [http://localhost](http://localhost) It prompts a download dialog for a filename xAfks0389.phtml, when I download it and open it, it has the php source code.

What could it be?

---

### Post by jorgepedret on 2007-06-14
Hey az, I'm trying that website you gave me (again) trying different installation methods.

When I tried to remove all the packages:

apache2 php5-mysql libapache2-mod-php5 mysql-server

I noticed at the end It says:
Removing apache2 ...
Removing php5 ...
Removing php5-mysql ...
Removing libapache2-mod-php5 ...
**Module php5 does not exist!**
Removing mysql-server ...

I seems that its not installing the php5 module? 

I'm so frustrated :S every time I try to migrate to linux happens the same thing, while on my other friend's machines work perfectly... (I'm doing this after giving birth with my wireless card which didn't worked well and configuring my dual monitor)

Please if anyone can help me I really appreciate it!

Thanks!

---

### Post by az on 2007-06-14
Remove skype and restart your computer.  Install the LAMP stack (using any method- either by selecting the packages or the task, it's the same.)

What does it say when you run:

sudo /etc/init.d/apache2 restart


That will describe the problem.

Never mind about php5 now.  That's not your problem.

---

### Post by jorgepedret on 2007-06-14
Thats the answer when I do : /etc/init.d/apache2 restart
* Forcing reload of web server (apache2)...                             [ OK ]

I think that the apache is working properly, I created an html page and it read it, I think that the problem now is the php. I will try the skype to discard this possibility. 

I tried downloading the php package from php.net and compiling it, but it prompts an error with some gcc stuff, even when the gcc is installed and working properly.

This is the response header when I go to [http://localhost/index.html](http://localhost/index.html)

Date: Fri, 15 Jun 2007 02:46:22 GMT
Server: Apache/2.2.3 (Ubuntu) PHP/5.2.1
Last-Modified: Thu, 14 Jun 2007 21:06:56 GMT
Etag: "6f05c8-160-1c535c00"
Accept-Ranges: bytes
Content-Length: 352
Content-Type: text/html; charset=UTF-8

200 OK

Thanks for your answer az.

---

### Post by jorgepedret on 2007-06-15
Ok, Im trying the xamp package [http://www.apachefriends.org/en/xampp-linux.html#374](http://www.apachefriends.org/en/xampp-linux.html#374), and I just figured it out that when I write [http://localhost/](http://localhost/) it prompts me with a download dialog for an phmtl file. But when I actually write the whole path [http://localhost/index.php](http://localhost/index.php) It brings me the correct file and interpret the php code! 

So is got to be something else, I checked the httpd.conf and it have these lines

<IfModule dir_module>
    #DirectoryIndex index.html
    # XAMPP
    DirectoryIndex index.html index.html.var index.php index.php3 index.php4
</IfModule>

---

### Post by az on 2007-06-15
> **jorgepedret said:**
> Thats the answer when I do : /etc/init.d/apache2 restart
* Forcing reload of web server (apache2)...                             [ OK ]

I think that the apache is working properly, I created an html page and it read it, I think that the problem now is the php. I will try the skype to discard this possibility. 

I tried downloading the php package from php.net and compiling it, but it prompts an error with some gcc stuff, even when the gcc is installed and working properly.

This is the response header when I go to [http://localhost/index.html](http://localhost/index.html)

Date: Fri, 15 Jun 2007 02:46:22 GMT
Server: Apache/2.2.3 (Ubuntu) PHP/5.2.1
Last-Modified: Thu, 14 Jun 2007 21:06:56 GMT
Etag: "6f05c8-160-1c535c00"
Accept-Ranges: bytes
Content-Length: 352
Content-Type: text/html; charset=UTF-8

200 OK

Thanks for your answer az.

Okay, forget about compiling php by yourself, the packages in main are supported and work fine.

You probably have tried to fix the problem and messed up a configuration.  Exaclty whan php and apache packages do you have instaled?  (exct names and versions)

php5 works out-of-the-box.  You do not need to do anything funky to get it working.  Nor would you need to do anything funky to fix it is you messed up the configuration.

---

### Post by hyper_ch on 2007-06-15
to activate php you have to enable it first in apache:

```

sudo a2enmod php5

```

Then reload apache and php5 should be working

---

### Post by jorgepedret on 2007-06-15
Ok, Im working now with XAMP because I need fast switch between php4 and php5 cuz im developing software for a company who has a php4 server.

Im working with this two versions: 
PHP 4.4.7 / PHP 5.2.2
Apache/2.2.4

As I said, php is working, apache is working because I see the php documents interpreted correctly when I go straight to them ([http://localhost/index.php](http://localhost/index.php)) the problem seems to be when I just to [http://localhost](http://localhost), it prompts a download dialog for a phtml file wich content is the source code of the index.php file that is suppose to show.

I already tried putting index.php first:
DirectoryIndex index.php index.html index.html.var index.php3 index.php4

Adding a .htaccess file in the root folder with this content:
DirectoryIndex index.php

And still not working.

:D Is not normal hehe, thanks for your help

---

### Post by hyper_ch on 2007-06-15
Are .htaccess files enabled (I think they are by default)... if not, you need to restart apache for the new config to be effective...

You can easily have php4/5 running at the same time.... install one as module and one as cgi and use different file endings or work with .htaccess for some folders to assign .php other than the default one...

---

### Post by drummingpariah on 2007-06-15
Heya everyone, I'm having a similar issue.  Any time I try to browse through my running apache2 server, once I get to the php file firefox spits out that I'm trying to read a PHTML file.  Pretty much everything is bone-stock, php5, apache2, and mysql-server as well as mysql are all installed (using apt-get install in the terminal).  It seems like apache2 just isn't recognizing the php at all.  The script I'm running is php5, I'm just not sure how to get it running correctly.  I've been banging away on this for about 4 hours now, and I've been through all the info posted so far, 

I've restarted apache2 after every step that I've tried, and while I'm very good at troubleshooting, I can't nail this one down.  Does anybody have a list of specific apt packages that are required (and those which might muck up the works) to at least get php working properly, then I can start messing with my mysql.  Thanks in advance!

---

### Post by hyper_ch on 2007-06-16
did you enable the php5 module in apache?

---

### Post by drummingpariah on 2007-06-17
I hadn't, but that solved it.  Man, I feel dumb now.  Thank you!

---

