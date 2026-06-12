---
title: "Installing MySql"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by superjacent on 2008-04-17
How do I install MySql.   I can't see any reference to it in the Add/Remove software program.    I'm also wanting to install PHP and Apache but can't find any references for these either.   For the time being though I'm more interested in getting MySql up and running.

Any help greatly appreciated.

---

### Post by Medieval_Creations on 2008-04-17
Run this command in a terminal and you should be all set.
```

sudo apt-get install apache2 php5 mysql-server mysql-client phpmyadmin

```

---

### Post by OffAxis on 2008-04-17
you can also just use the tasksel command to display a list of common multi-package installs.
```
sudo tasksel
```

LAMP will be your linux, apache, mysql, php configuration.

---

### Post by t3hi3x on 2008-04-17
> **OffAxis said:**
> you can also just use the tasksel command to display a list of common multi-package installs.
```
sudo tasksel
```

LAMP will be your linux, apache, mysql, php configuration.

Very nice. Learn something everyday.

---

### Post by BatsotO on 2008-04-17
Personally, I prefer synaptic over add/remove program. I begin to wonder why we need that add/remove thing when we have synaptic.

---

### Post by Medieval_Creations on 2008-04-17
> **BatsotO said:**
> Personally, I prefer synaptic over add/remove program. I begin to wonder why we need that add/remove thing when we have synaptic.

My best guess is choice... That and I would imagine that it's easier for a Windows user coming over to Linux to understand and use.

---

### Post by .nedberg on 2008-04-17
> **OffAxis said:**
> you can also just use the tasksel command to display a list of common multi-package installs.
```
sudo tasksel
```

LAMP will be your linux, apache, mysql, php configuration.

Didn't know about that one. Very good indeed! Been looking for somthing like that for a while! Thanks!

---

### Post by SunnyRabbiera on 2008-04-17
> **BatsotO said:**
> Personally, I prefer synaptic over add/remove program. I begin to wonder why we need that add/remove thing when we have synaptic.

Yeh the add/ remove applet is a little shaky, but good for beginners...
but if you want more advanced tools synaptic is best along with apt-get

---

### Post by superjacent on 2008-04-17
Thank you all, the above worked.   Next I've got to figure out how to start & use Apache.

---

### Post by Medieval_Creations on 2008-04-17
Once you install apache (using any of the ways/appz stated above) it should be running immediately after you install it.

To test it all you need to do is type this into your web browser.

```
http://localhost/apache2-default/
```

You should see a "It Works" page if everything is running properly.

---

### Post by superjacent on 2008-04-17
> **Medieval_Creations said:**
> Once you install apache (using any of the ways/appz stated above) it should be running immediately after you install it.

To test it all you need to do is type this into your web browser.

```
http://localhost/apache2-default/
```

You should see a "It Works" page if everything is running properly.

Thanks, yes the above works.

To what directory on my system does localhost resolve to?

---

### Post by Medieval_Creations on 2008-04-17
I'm pretty sure it's /var/www.

---

### Post by superjacent on 2008-04-17
> **Medieval_Creations said:**
> I'm pretty sure it's /var/www.

Yep, found it, thank you.

---

### Post by sanus|art on 2008-04-17
I just feel that I have to mention [xampp]("http://www.apachefriends.org/en/xampp-linux.html") here.
:)

---

### Post by BatsotO on 2008-04-19
you can create public_html directory in you home directory

---

### Post by superjacent on 2008-04-19
> **BatsotO said:**
> you can create public_html directory in you home directory
How is that done.   Which configuration setting do I adjust.

---

### Post by sanus|art on 2008-04-19
Create the desired folder, and point to that folder in 'httpd.conf' file (in two places):

Line 170 +/- 
DocumentRoot "/path/to/the/www"

Line 207 +/-
<Directory "/path/to/the/www">

---

### Post by superjacent on 2008-04-21
Where would I find 'httpd.conf'.   Searching for it on my system revealed no results.

---

### Post by bartcramer on 2008-04-21
This link might be very helpful to you: 

[http://doc.ubuntu.com/ubuntu/serverguide/](http://doc.ubuntu.com/ubuntu/serverguide/)

It should get you running for a lot of (rather basic) questions you're asking. 

Good luck!

---

### Post by sanus|art on 2008-04-21
> **superjacent said:**
> Where would I find 'httpd.conf'.   Searching for it on my system revealed no results.

Differs from apache version, try:
```
sudo gedit /etc/httpd/conf/httpd.conf
```

---

### Post by superjacent on 2008-04-21
> **bartcramer said:**
> This link might be very helpful to you: 

[http://doc.ubuntu.com/ubuntu/serverguide/](http://doc.ubuntu.com/ubuntu/serverguide/)

It should get you running for a lot of (rather basic) questions you're asking. 

Good luck!
Thanks, I've since found where the file resides which is currently in /etc.   For the life of me I don't know why the file browser couldn't find that file.   I correctly started the search from the computer level not my home directory.   Looking up a section in that document you provided, which didn't specifically  answer my question but pointed me in the right direction revealed the file.   

These might be rather simple (roll eyes) type of questions but is very frustrating when the search doesn't work - so called simple stuff.

I do appreciate your response and have bookmarked that document.   I'm just venting a little out of frustration (not at any person).

---

### Post by superjacent on 2008-04-21
> **sanus|art said:**
> Differs from apache version, try:
```
sudo gedit /etc/httpd/conf/httpd.conf
```

Thanks.   I've found that file but it's an empty file.   Searching around the particular directory and I've come across a folder /etc/apache2/sites-enabled which contains this file, 000-default

Perusing that file, starts off

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>

```

I'm half assuming that I change the document root in this file.

---

### Post by sanus|art on 2008-04-21
> **superjacent said:**
> Thanks.   I've found that file but it's an empty file.   Searching around the particular directory and I've come across a folder /etc/apache2/sites-enabled which contains this file, 000-default

Perusing that file, starts off

```
NameVirtualHost *
<VirtualHost *>
    ServerAdmin webmaster@localhost
    
    DocumentRoot /var/www/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>

```I'm half assuming that I change the document root in this file.

You better not as [FONT=Courier New]httpd.conf[/FONT] is the "boss" and it changes all his subfiles according to his settings, try in [FONT=Courier New]/usr/local/apache2/bin[/FONT]

---

### Post by superjacent on 2008-04-21
> **sanus|art said:**
> You better not as [FONT=Courier New]httpd.conf[/FONT] is the "boss" and it changes all his subfiles according to his settings, try in [FONT=Courier New]/usr/local/apache2/bin[/FONT]

There is no /usr/local/apache2/bin directory.   All I have, as far as I can tell, is /etc/apache2 directory with these sub-directories;
conf.d
mods-available
mods-enabled
sites-available
sites-enabled

and these files,

apache2.conf
enwars
httpd.conf (empty)
ports.conf

---

### Post by sanus|art on 2008-04-21
How about:
```
sudo gedit /usr/local/apache/conf/httpd.conf
```Anyway how did you installed the server?
Did you started the server? As in some cases it is auto-generated.

---

### Post by hmbuhler on 2008-04-26
i couldn't get apt-get to work:

michael@ubuntu-dell-laptop:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mysql-server
michael@ubuntu-dell-laptop:~$ 

what am i not doing?

thanks,
mike

---

### Post by Medieval_Creations on 2008-04-27
I can't remember exactly which repository MySQL is in, I think it's one of the *verses.  Double check your apt sources list (/etc/apt/sources.list) and make sure you have the all the multiverse and universe repositories.  Here's what I have in mine.

```

## Ubuntu 7.10
deb http://mirrors.cs.wmich.edu/ubuntu/ gutsy main restricted
deb-src http://mirrors.cs.wmich.edu/ubuntu/ gutsy main restricted
deb http://mirrors.cs.wmich.edu/ubuntu/ gutsy-updates main restricted
deb-src http://mirrors.cs.wmich.edu/ubuntu/ gutsy-updates main restricted
deb http://mirrors.cs.wmich.edu/ubuntu/ gutsy universe
deb-src http://mirrors.cs.wmich.edu/ubuntu/ gutsy universe
deb http://mirrors.cs.wmich.edu/ubuntu/ gutsy multiverse
deb-src http://mirrors.cs.wmich.edu/ubuntu/ gutsy multiverse
deb http://mirrors.cs.wmich.edu/ubuntu/ gutsy-security main restricted
deb-src http://mirrors.cs.wmich.edu/ubuntu/ gutsy-security main restricted
deb http://mirrors.cs.wmich.edu/ubuntu/ gutsy-security universe
deb-src http://mirrors.cs.wmich.edu/ubuntu/ gutsy-security universe
deb http://mirrors.cs.wmich.edu/ubuntu/ gutsy-security multiverse
deb-src http://mirrors.cs.wmich.edu/ubuntu/ gutsy-security multiverse

```

If they aren't there add them and then do:
```
sude apt-get update
```

Then try to install mysql again.

---

### Post by hmbuhler on 2008-04-27
AAARGH!

Well, they aren't in there.  I get this:

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

Lots and lots of those, just a snippet.

Now, since I'm new (and possibly slow), how would I go about getting the required "verses" downloaded and installed so that I can then perform the final apt-get routine to install?  

Thanks for your help M_C, but I'm not out of the woods yet!

Mike

---

### Post by Medieval_Creations on 2008-04-27
Hmmmm, well they have to be in one of them...

First question that I should have asked is which version of Ubuntu are you running?  Gutsy, Hardy, or other?

It's not a major thing, but we want to make sure that the name (gutsy / hardy) in the sources.list match the version you are running.

I've attached a copy of my sources.list file (gutsy), which should work.  I have mysql installed.

Steps:
1.) Download the file and save it whereever you like.
2.) Lets make a back up of your current sources.list file, just in case.
```
sudo cp /etc/apt/sources/sources.list /etc/apt/sources/sources.list.old
```
3.) Now we'll replace your sources file with the new one.
```
sudo cp gutsy.sources.list.wmich.txt /etc/apt/sources.list
```
4.) Now we'll need to run an update.
```
sudo apt-get update
```
5.) Hopefully there were no errors with the update and everything ran smoothly, now we can try to install MySQL.
```
sudo apt-get install mysql-server mysql-client
```

That should work.
Let me know how it works out and we'll go from there.

---

### Post by hmbuhler on 2008-04-30
Eureka!  

Thanks, M_C, it's installed...the rest is up to me :)

Check your personal messages...

Mike

---

