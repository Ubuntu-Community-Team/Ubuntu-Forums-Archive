---
title: "Basic Apache twaking help please"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by gingerj on 2006-12-19
Hi all,

I've recently installed apache2 via this command:

sudo apt-get install apache2

Which worked great then to confirm the install I searched the forum to see how I could check that apache is working. So I've typed in [http://localhost](http://localhost) and that just goes to a default apache directory, which contains a hyperlink to go to a apache2 page serverd in my var directory. I've also double checked to see that it's working by going to system>adminstration>services and it's in there and checked.

So I know apache2 is completely working, my next port of call is to get apache2 to look at another directory to check for files. So I can do this for example:

[http://localhost/WebDev/index.html](http://localhost/WebDev/index.html)

I've used this link that's listed in a previous thread here:

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Apache_HTTP_Server_for_HTTP_.28Web.29_Server_service](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Apache_HTTP_Server_for_HTTP_.28Web.29_Server_service)

But I can't seem to get this to work I get an error message when in the terminal and when gedit opens I see a blank file. This is the error message that I get:

> 
(gedit:6131): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Using this cmd:

gksudo gedit /etc/apache2/conf.d/alias

Any ideas? Or can I just go ahead and save this new file? 

Many thanks!

---

### Post by gingerj on 2006-12-19
err any help would be greatly appreciated.

---

### Post by gingerj on 2006-12-19
RIght I've royally ****** this thing up:

Due to the lack of response I thought hell I'll just have a go:

So I opened the conf file and it opened the blank doc I put this in:

> 
Alias /home/james/WebDev/

<Directory /home/james/WebDev/>
  Options Indexes FollowSymLinks
  AllowOverride All
  Order allow,deny
  Allow from all
</Directory>


Then restarted apache2, after that I went to the browser and checked the localhost, I got a page cannot be displayed. I've tried to revert back to the blank document that originally was there I presume.

BY doing the gedit cmd to open up the conf.d/alias file, and erasing what I orginally put in. Then in the terminal tried to restart the server I now get a new error message:

> 
 * Forcing reload of apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName


Can anyone help, all I wanna do is change the dir everything is so damn hard in Ubuntu, I can't even add my own file to the var/www cos it won't paste via the gui. so you've gotta go to the terminal but as a new comer i've got no idea how to change the file permissions nor how to move anything?

Oh btw is everything in Ubuntu so painful to get working? As if it is I might as well give up now, literally I cannot do anything without reading a faq/using the forum, there's such a steep learning curve that it's really off putting. The official Ubuntu book really doesn't gear you up for actually using the system more than the real basics which are painfully obvious.

Everything needs manual editing, terminal knowledge or constant help from members on the forum. It's seriously difficult to get anything done ](*,) I can't even get one app to install that's not in the repository ONE app, seriously coming from a windows user I don't know how any of you guys can put up with this.

Many thanks!

---

### Post by David Corrales on 2006-12-19
Being a sysadmin is not about clicking next, next, next. If you want to properly administer an apache webserver, you need to read its help files, online tutorials, etc. You can't expect to get a full comprehensive answer in a single forum post.

---

### Post by az on 2006-12-19
> **gingerj said:**
> 

So I know apache2 is completely working, my next port of call is to get apache2 to look at another directory to check for files. So I can do this for example:


Change the document root in the apache-default site (/etc/apache2/sites-available).  Or create a different site and make it use the files from somewhere else.

---

### Post by az on 2006-12-19
> **gingerj said:**
> I don't know how any of you guys can put up with this.


I find windows much more of a pain in the *** to use.

As for your issues,

You need permissions to put files in any other place than you home folder.  You typically don't even run a GUI on a server.  That makes it a more secure and better server.  

I guess linux is not for you.

---

### Post by daniel of sarnia on 2006-12-19
> **azz said:**
> 
I guess linux is not for you.

Yeah Linux is only used for 85% servers in the world. If you're of the 15% that likes paying too much for software and slowing down the server with a GUI Windows is for you!

---

### Post by gingerj on 2006-12-19
I'm not planning on using this as a server as such I just want all these services installed so I can continue to work from home as when I need to. I'm a webdeveloper so at work I have every pre-installed for me and I can just get my head down.

I don't want to be a server admin, I think you've got the wrong end of the stick. Getting apache working is just what I thought was a minor detail. Before getting PHP/RUBY/SQL working on Ubuntu box.

I presumed one forum post was enough just to help me tackle these errors as once its working I'm not intending to touch any of it ever again.

Cheers

---

### Post by gingerj on 2006-12-19
Fixed it instead of trying to edit the file listed in [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy), I manually edited the /apache2/sites-available/default file with a sudo gedit command. It works great!

Many thanks to everyone who replied to this thread, and helped me to get this thing done in some way.

---

