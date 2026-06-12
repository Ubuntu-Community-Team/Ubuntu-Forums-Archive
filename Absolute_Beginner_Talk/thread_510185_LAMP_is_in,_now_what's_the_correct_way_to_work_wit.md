---
title: "LAMP is in, now what's the correct way to work with /var/www folder?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-07-26
LAMP is in, now what's the correct way to work with /var/www folder?
I can't create files and folders in /var/www.
The permission for this folder is USER/GROUP = root/root.
And I want to create a link from this folder on my Desktop to quickly access my workfiles which I'm not allowed to create files and folders on. :confused:

I've seen this code somewhere and used it, but some Linux veterans said that it's not recommended to do so that it's not the most secure way to do things.
```
sudo chown -R $USER:$GROUP /var/www
```
Since I think I got trojaned a few weeks ago and it locked me out from my /root Ubuntu indefinately I can't confirm if it really was a trojan that crashed my Ubu for good.  But in case that's true.

What's the proper way to work with /var/www the secure way that is?  Without using this code.
```
sudo chown -R $USER:$GROUP /var/www
```
I don't have to ( Alt -F2 ) 
```
gksudo nautilus
``` everytime I want to edit my *.html s, *.php s, create files and folders on /var/www do I?

---

### Post by bbzbryce on 2007-07-26
> **jingo811 said:**
> LAMP is in, now what's the correct way to work with /var/www folder?

I'm not sure if this is the proper way, but I created a folder in my user account /home/bryce/www/ and then for each folder (site) in /home/bryce/www I created a symbolic link from /var/www/someSite to /home/bryce/www/someSite.

The command to do this:

```
sudo ln -s /home/bryce/www/test/ /var/www/test
```

Then of course I had to configure apache to use these sites appropriately but as far as it's concerned everything appears to be in /var/www but has my user permission.

---

### Post by indytim on 2007-07-26
Change BOTH the owner and group in /var/www to your user id.

IndyTim

---

### Post by jingo811 on 2007-07-26
I think it worked however the folder has a lock on it.
```
 sudo ln -s /var/www/sp /home/mikey/Desktop/html/sp
```

Which brings me back to the unsecure command which isn't recommended, if I want to unlock that folder for edit.
```
sudo chown -R $USER:$GROUP /var/www
```
What should I do instead of chown?  What's the secure way to work?

---

### Post by indytim on 2007-07-26
By secure, are you referring to not allowing access to apache from the outside?  If so, then you will need to adjust the listen setting (see the LAMP how-to for details on setting this). 

IndyTim

---

### Post by jingo811 on 2007-07-26
> Change BOTH the owner and group in /var/www to your user id.

IndyTim
OK if you say so!  I'm pretty sure someone told me not to unfortunately I couldn't find that thread and refer to, so unless there's any objection I'll go for it.

---

### Post by bbzbryce on 2007-07-26
> **jingo811 said:**
> I think it worked however the folder has a lock on it.
```
 sudo ln -s /var/www/sp /home/mikey/Desktop/html/sp
```

I see now. There really isn't anything wrong with having the files/folders of your webserver owned by a standard user. The only reason /var/www is owned by root is so that a regular user cannot delete it. If you are the only one working on this machine then just chown -R /var/www, however I prefer keeping files on in my home directory to that method.

If you're really insistent on maintaining the root:root property on all the web files then I'm not sure how to proceed.

---

### Post by jingo811 on 2007-07-26
Yeah I guess CHOWNing root/root to your current User/Group name won't make it less secure than if I've been working on WAMP where you don't deal with file permissions.
Tnx for the helps ppl.

---

### Post by az on 2007-07-26
Edit the default site in /etc/apache2/sites-available/default and make the documentroot point to a folder in your home drive.

Then, just make sure that the contents of that folder are world-readable.

Since the www-data user does not have the ability to write to your home folder, that should be safe.

---

### Post by jingo811 on 2007-07-26
> Then, just make sure that the contents of that folder are world-readable.
Define world readable?
Does it mean that the folder should be CHMOD to 755, 777 or do you mean something else?

> Since the www-data user does not have the ability to write to your home folder, that should be safe.
Who is this User/Group www-data person?  I thought it was just some example name you used in the LAMP tutorial were I the reader was supposed to change to my current User/Group name.

---

### Post by az on 2007-07-26
> **jingo811 said:**
> Define world readable?
Does it mean that the folder should be CHMOD to 755, 777 or do you mean something else?


Who is this User/Group www-data person?  I thought it was just some example name you used in the LAMP tutorial were I the reader was supposed to change to my current User/Group name.

744

and www-data is the user that apache runs as.  Do not change it.

---

### Post by jingo811 on 2007-07-26
all-right Captain.

---

### Post by jingo811 on 2007-07-27
Hey Az I'm still doing something wrong can you help? :(


**/etc/apache2/sites-available/default**
```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot **/home/mikey/Desktop/html/**
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
```


I did **chmod -R 744 /home/mikey/Desktop/html/** and this is the **ls -l** for my html folder.
```
drwxr--r--  6 mikey mikey   4096 2007-07-26 17:51 html
```


When I open up Firefox and type in **localhost** I get this error can you see what I've done wrong?
[COLOR="Red"]403 Forbidden[/COLOR]
> Forbidden
You don't have permission to access / on this server.
Apache/2.2.3 (Ubuntu) PHP/5.2.1 Server at localhost Port 80


I didn't have any trouble accessing /var/www/ = **localhost** before I changed the DocumentRoot is there something else that needs to be done?
I've already done **sudo /etc/init.d/apache2 force-reload** on Apache and even rebooted the PC.  But I still get Error 403.

---

### Post by twistedtwig on 2007-07-27
Don't know if this is wrong or not but I was told once to use nobody:nogroup

---

### Post by az on 2007-07-27
> **jingo811 said:**
> Hey Az I'm still doing something wrong can you help? :(


**/etc/apache2/sites-available/default**
```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot **/home/mikey/Desktop/html/**
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
```


I did **chmod -R 744 /home/mikey/Desktop/html/** and this is the **ls -l** for my html folder.
```
drwxr--r--  6 mikey mikey   4096 2007-07-26 17:51 html
```


When I open up Firefox and type in **localhost** I get this error can you see what I've done wrong?
[COLOR="Red"]403 Forbidden[/COLOR]



I didn't have any trouble accessing /var/www/ = **localhost** before I changed the DocumentRoot is there something else that needs to be done?
I've already done **sudo /etc/init.d/apache2 force-reload** on Apache and even rebooted the PC.  But I still get Error 403.


My bad.  It should be 755 for the directory.  If the x bit is not set, you can't list files in the directory.

---

### Post by jingo811 on 2007-07-27
**ls -l** for /home/mikey/Desktop/html/
```
drwxr-xr-x  6 mikey mikey   4096 2007-07-26 17:51 html
```
I restarted Apache and also rebooted my PC I still get that 403 Forbidden error when typing **localhost** into Firefox.

I think it's something with the **DocumentRoot** change in **/etc/apache2/sites-available/default**.  Don't I have to edit **gksudo "gedit /etc/apache2/apache2.conf"** also?
But I already searched for "documentroot" in that file it couldn't find any.

---

### Post by jingo811 on 2007-08-07
Can somebody who managed to change their DocRoot from** /var/www/ **to somewhere in their **/home** directory give me a step by step tutoring.  I can't seem to make it work even after following the previous discussed procedures.

If noone knows then I must reluctantly break the rule and change user/group **data-www/data-www** into my own user account name i.e. mikey/pc1. in order to make LAMP  operational again. :confused:

---

### Post by Pinger05 on 2007-08-07
Jingo - This is directly from my personal notes about this issue.  Check out the part at the bottom about the permissions.


> Problem:  I have an Apache2 server running Ubuntu 7.04 Server edition and I want to have it to host two web sites.  One website is [www.watson.com](www.watson.com) and the other is [www.pinger05.com](www.pinger05.com).  To accomplish this I have to create two virtual hosts on the Apache2 server.
First we need to create a pointer in the sites-available directory.  For no particular reason we will call the file virtual.  To make this happen type in the following:
cd /etc/apache2/sites-available
sudo nano virtual

Inside the file watson type:
	NameVirtualHost *
		<VirtualHost *>
			ServerName watson.com
			ServerAlias watson.com *.watson.com
			DocumentRoot /var/www/watson/
		<VirtualHost>
		<VirtualHost *>
			ServerName pinger05.com
			ServerAlias pinger05.com *.pinger05.com
			DocumentRoot /var/www/pinger05/
		</VirtualHost>

	What does it all mean?  NameVirtualHost * creates the virtual host.  If you wanted to you could make it the IP address of the computer.  You could have even named it bob if you wanted to.  Best to just use * though.
	Under NameVirtualHost * is <VirtualHost *> </VirtualHost>.  Between these two tags you are configuring the virtual host.  There are lots of options to choose from.  In the /etc/apache2/sites-available there is a default file.  That file has all the options.  What do they mean?  Beats me.
	Required options:  You need to specify the name of the virtual server by using the ServerName call.  Additionally ServerAlias will tell it to resopond to other things.  You could have made you website respond to [www.billybob.com](www.billybob.com) if you told it to.  Finally you need to tell it where to go.  Hence the DocumentRoot /var/www/pinger05.
	Now we need content to the sites.  Create the directories then add the content as you see fit.  The directories can be anywhere.  Good practice is to put them in the /var/www folder.  Bad practice is to have them in the /home directory.

cd /var/www
sudo mkdir watson
sudo mkdir pinger05

Now put content into the two directories.  Any files in the watson and pinger05 directories need to have permissions of 755.  To make that happen run:

sudo chmod 755 *filename*

	For sub directories of your site you will need to set permissions of 711.  To make that happen run:

sudo chmod 711 *directory name*

	So now the virtual hosts are created and the content is added.  Let’s run this puppy!  Type in:

sudo a2ensite virtual
sudo /etc/inet.d/apache2 restart

	You should get an error stating something along the lines of “Cannot resolve watson”.  If you get something else you might have to do some serious troubleshooting.


---

### Post by jingo811 on 2007-08-07
Hmmm....I can't say I understand this virtual host file thing.  But when it comes to the CHMOD part.    It doesn't look that un-similar to what I've tried before and your post seems to have even more strict CHMOD rules 711 compared to 755, 744 that I tried before on /var/www.

Maybe I'm asking this question wrong?  But it seems like you guys do this from a dedicated LAMP server point of view. ** I like to manage and edit my *.html and *.png files on the fly.**  Like you could do in Windows' version of LAMP or WAMP.  
To achieve that I've only found out 2 methods so far which seems to be the improper ways of doing things.  The first one is to rename USER/GROUP = www-data, to your own account.  The other is to CHMOD /var/www 777.

Is there a proper way of accomplishing this in LAMP.  Or should I fall back on those improper ways of doing things.
( I don't want to always have to do: Alt-F2, gksudo nautilus, browse to /var/www/somefolder, to work on my webpages )

---

### Post by indytim on 2007-08-07
I hope I'm not  missing something in your posting and subsequent threads.  If you're using the LAMP for development only (local use), why don't you just change the user and group affiliation on /var/www to your user id.  Put your server files under var/www and be done with it.  This is the way I have done it on 3 different Lx LAMP installations.

IndyTim

---

### Post by Pinger05 on 2007-08-07
> **jingo811 said:**
>  
( I don't want to always have to do: Alt-F2, gksudo nautilus, browse to /var/www/somefolder, to work on my webpages )

I keep my webpage on a Ubuntu laptop.  When I update the webpage I update from that laptop then load it to the /home/dan folder of the server using an SSH network share to the server.  Once copied, I move the modified website to the /var/www/pinger05/ and then do a chmod 755 *.

To do it on the fly you will have to navagate somewhere...why not /var/www/?  Otherwise I think you are at an impass.  Sorry if I wasnt much more help

---

### Post by morcom on 2007-08-07
Thanks for the info Pinger05 - makes a lot of sense to me (old newbe).
Just a couple of typos that threw me bit
[I]  Inside the file[COLOR="Red"] virtual[/COLOR] type:
  NameVirtualHost *
  <VirtualHost *>
  ServerName watson.com
  ServerAlias watson.com *.watson.com
  DocumentRoot /var/www/watson/
  [COLOR="Red"]</VirtualHost>[/COLOR]
  <VirtualHost *>
  ServerName pinger05.com
  ServerAlias pinger05.com *.pinger05.com
  DocumentRoot /var/www/pinger05/
  </VirtualHost>
[/I]
also the last command should be
*sudo /etc/[COLOR="Red"]init.d[/COLOR]/apache2 restart*
However, thank for your input as i now have a better understanding.
I'm working out why I keep getting the following
***Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName*** for each of the virtual hosts but not for the default host.
Trying to work out how localhost works...because that does work...
Thanks again

---

### Post by jingo811 on 2007-08-09
> If you're using the LAMP for development only (local use), why don't you just change the user and group affiliation on /var/www to your user id. Put your server files under var/www and be done with it. This is the way I have done it on 3 different Lx LAMP installations.

Yeah so I'm gonna go with this since it's the only answer I really understand.  All the other explanations is a little too advanced for me.

---

### Post by jingo811 on 2007-08-16
> I hope I'm not missing something in your posting and subsequent threads. If you're using the LAMP for development only (local use), why don't you just change the user and group affiliation on /var/www to your user id. Put your server files under var/www and be done with it. This is the way I have done it on 3 different Lx LAMP installations.

IndyTim

That didn't seem to work anymore on Feisty.  It worked when I was on Dapper 6.06.
In Feisty when I do this in terminal.

```
pingu@renaissance:/var$ **ls -l**
total 48
drwxr-xr-x  2 root  root  4096 2007-08-13 10:38 backups
drwxr-xr-x 18 root  root  4096 2007-08-16 13:11 cache
drwxrwxrwt  2 root  root  4096 2007-04-10 09:46 crash
drwxr-xr-x  2 root  root  4096 2007-04-15 14:01 games
drwxr-xr-x 49 root  root  4096 2007-08-16 13:11 lib
drwxrwsr-x  2 root  staff 4096 2007-04-12 11:11 local
drwxrwxrwt  3 root  root    60 2007-08-16 14:21 lock
drwxr-xr-x 13 root  root  4096 2007-08-16 14:21 log
drwxrwsr-x  2 root  mail  4096 2007-04-15 13:48 mail
drwxr-xr-x  2 root  root  4096 2007-04-15 13:48 opt
drwxr-xr-x 16 root  root   720 2007-08-16 14:22 run
drwxr-xr-x  8 root  root  4096 2007-08-16 13:11 spool
drwxrwxrwt  3 root  root  4096 2007-08-16 11:15 tmp
drwxr-xr-x  3** pingu pingu** 4096 2007-08-16 14:00** www**
pingu@renaissance:/var$ 
```

Things seems to be in order.  But when I open up the /var/www catalog via Nautilus and check the folder permissions it still says **root/root** I can't even create a folder nor a file in /var/www :confused:
How in the world am I supposed to develop PHP, MySQL webpages if I can't even create/delete/rename a simple textfile in /var/www?

---

### Post by jingo811 on 2007-08-16
Feisty is weird, just because I wrote the above it started to work like intended again 5 minutes later :)  So business as usual.

---

