---
title: "Complete n00b, wants to set up Apache2"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by khwang on 2005-06-27
I've installed Ubuntu 5.04 off the pre-packaged CD, and it works great.  I used the synaptic package manager to install apache2, mysql, php, perl.

Now what do I do??  I found a "get started with apache2" article on devshed:
[http://www.devshed.com/c/a/Apache/Getting-Started-with-Apache-2-0-Part-1/](http://www.devshed.com/c/a/Apache/Getting-Started-with-Apache-2-0-Part-1/)

... but I didn't have to compile anything from source.  It mentions this path:

$ /usr/local/apache/bin/apachectl start

But I didn't find an 'apache' folder in /usr/local/

When I shut down my machine, one of the tasks listed on the screen is the apache server being shut down.  So it's gotta be somewhere, heh. 

I am a complete n00b to Linux, Ubuntu, and Apache.  So if you could just give me a few introductory tips, I can find the rest of my answers on the web.  I'd like to set up a home server so I can fool around with php, perl and mysql.

Thanks for your help.  :)

---

### Post by Ride Jib on 2005-06-27
If you browse to /var you will see a directory named "www." Place all your web files, etc. in this directory. 

Then point your webbrowser to [http://localhost](http://localhost) or [http://127.0.0.1](http://127.0.0.1) and you should see your index.html/php page. 

If you are behind a router, you will need to port forward port 80 to your machine. Then you can direct friends to your site via your ip address ([http://111.11.11.11](http://111.11.11.11))

Good luck!

---

### Post by StacyWebb on 2005-06-27
it (the startup) will be located in /etc/init.d/ then you will see apache2

do the following

cd /etc/init.d/
sudo ./apache2 start   

to stop the server run
./apache2 stop



then follow Ride_jb's instructions and all should go well. Really easy to do.

---

### Post by Kvark on 2005-06-27
There is nothing you need to configure, everything works after you installed it.

Some things that you may or may not want to change:

* Set up user accounts for mysql, right now it got only a root account with no password. Use an administrator tool for this. It isn't really an issue though unless you set mysql to accept connections from the outside or if you have not taken proper steps to avoid sql injection from your website.

* If you want to put your website anywhere else then /var/www/, then replace both "/var/www/" mentioned in /etc/apache2/sites-available/default with whatever directory you want to put the website in,

* If you use the server for development and don't want outsiders to see your half finished site, (and perhaps test for example sql inject on it's half finished security) change "Listen 80" to "Listen 127.0.0.1:80" in /etc/apache2/ports.conf.

---

### Post by khwang on 2005-06-27
Thanks for the info! :)  Here are my follow-up questions:

> Then point your webbrowser to [http://localhost](http://localhost) or [http://127.0.0.1](http://127.0.0.1) and you should see your index.html/php page.

So by default, it will recognize an index.html or index.php file?  How can I get it to recognize some other file, like home.html?  Something to do with htaccess?

> 	
cd /etc/init.d/
sudo ./apache2 start

to stop the server run
./apache2 stop


Ah, excellent.  Thanks. \\:D/ 


> 
* Set up user accounts for mysql, right now it got only a root account with no password. Use an administrator tool for this.

what administrator tool?  In Gnome, I do Applications > System Tools > Root Terminal, is this correct?

> 
* If you use the server for development and don't want outsiders to see your half finished site, (and perhaps test for example sql inject on it's half finished security) change "Listen 80" to "Listen 127.0.0.1:80" in /etc/apache2/ports.conf.


what is sql injection?

---

### Post by Mr. Electric Wizard on 2005-06-28
[QUOTE=Kvark]
* If you want to put your website anywhere else then /var/www/, then replace both "/var/www/" mentioned in /etc/apache2/sites-available/default with whatever directory you want to put the website in,
[/QUOTE]

I tried this, to put the /www directory in my /home folder ,but when I change the /etc/apache2/sites-available/default file to point to my /home directory it doesn't work...
Is there any other settings that I should change?
BTW, it works great in /var/www/ but it would be nice for my regular user permissions to be able to edit the html.

---

### Post by Kvark on 2005-06-28
[QUOTE=khwang]So by default, it will recognize an index.html or index.php file?  How can I get it to recognize some other file, like home.html?  Something to do with htaccess?[/QUOTE]

Can't remember how to do that one but I'd name the file index.html because if you later move the site to another server that someone else configured, then it won't use other filenames as index.

[QUOTE=khwang]what administrator tool?  In Gnome, I do Applications > System Tools > Root Terminal, is this correct?[/QUOTE]

The command line terminal has nothing to do with mysql. There are many administration tools for mysql. For example [PhpMyAdmin](www.phpmyadmin.net).



[QUOTE=khwang]what is sql injection?[/QUOTE]

You should study [http://www.php.net/security](http://www.php.net/security) before using php, and corresponding documents for other languages before using them.

[QUOTE=Mr. Electric Wizard]I tried this, to put the /www directory in my /home folder ,but when I change the /etc/apache2/sites-available/default file to point to my /home directory it doesn't work...
Is there any other settings that I should change?
BTW, it works great in /var/www/ but it would be nice for my regular user permissions to be able to edit the html.[/QUOTE]

It should look like this. Both "/website/directory/" should ofcourse be changed to the directory you want it in....

> 	DocumentRoot /website/directory/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /website/directory/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

No other part of that file needs to be changed.

---

### Post by Mr. Electric Wizard on 2005-06-28
So, should /home/user/www be changed to /home/eric/www or be left as user?

---

### Post by Kvark on 2005-06-28
[QUOTE=Mr. Electric Wizard]So, should /home/user/www be changed to /home/eric/www or be left as user?[/QUOTE]

Yes.

Was stupid of me to use that path as example, edited my post above to be clearer.

---

### Post by Mr. Electric Wizard on 2005-06-28
That's what I'm saying though, when I change the path in this file to:
/home/eric/www/  it won't work...
It will only work with /var/www/

I am moving the folder when I do this of course...
Any other ideas?

---

### Post by Kvark on 2005-06-28
[QUOTE=Mr. Electric Wizard]That's what I'm saying though, when I change the path in this file to:
/home/eric/www/  it won't work...
It will only work with /var/www/

I am moving the folder when I do this of course...
Any other ideas?[/QUOTE]

Odd, it works for me...

Did you restart apache to make it read the new config files after you made the change?

---

### Post by Mr. Electric Wizard on 2005-06-28
Funny, I just thought about that...
I'll try when I get home from work!
I bet that will fix it...

---

### Post by Mr. Electric Wizard on 2005-06-28
Sho Nuff, that fixed it!
Thanks man! :razz:

---

### Post by khwang on 2005-07-12
I've set up another machine with Ubuntu 5.04, installed Apache2.  I used sudo gedit ports.conf and changed it to Listen 5355 but that doesn't work.  Users can still access my machine by going to [http://192.168.x.x](http://192.168.x.x)  but I want them to go to [http://192.168.x.x:5355](http://192.168.x.x:5355)

I tried different port numbers, like 85, 535, 5355.  Is there a range of acceptable port numbers?

---

### Post by czambran on 2005-07-12
u need to change the port Apache listens to by editing the httpd.conf file.

---

### Post by khwang on 2005-07-12
But it's the ports.conf file that has "Listen 80".  :-?

---

