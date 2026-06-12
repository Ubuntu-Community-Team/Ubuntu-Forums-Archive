---
title: "[SOLVED] help with setting up website"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by charlier653 on 2007-07-25
I finally got my maching to dual boot winXP and dapper.

I havew been hosting a website on win, and need to set up same in ubuntu.

apache is installed and working.

trying to get the contents of htdocs(win) into the /var/www in ubuntu.

tried changing permissions for the XP drives.....nogo.

tried burning htdocs to cd, then copy to /var/www.......again no joy.

cd burned ok, cd drive mounts auto on boot, shows proper folder and files.

getting a little frustrated here.](*,)](*,)](*,)

what cli commands do i need to use to accomplich my goals?

or is there a way to point apache directly to the original folder in the XP drives?[-o<[-o<[-o<

---

### Post by DBStevens on 2007-07-25
Something like this for /etc/apache2/sites-enabled/000-default would at least put the directory under your userid and remove the need to play sudo/whatever all of the time or if you wish to put it in a directory in /var/www/ you'll have to set that directory up and change the ownership to your user id in order to use it without sudo/what ever all of the time.   You have other things to change so that Apache uses your userid if you have an application that needs to modify files on the server.  Otherwise Apache will use the abilties granted to its primary userid which is www-data when installed through Ubuntu's repos.  Be careful  in this area if you need to run multiple sites as it is possible for one site to clobber the others.    

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/userid/myhtdocs/
	<Directory />
		Options -Indexes FollowSymLinks Includes 
		AllowOverride None
	</Directory>

	ScriptAlias /cgi-bin/ /home/userid/myhtdocs/cgi-bin/
	<Directory "/cgi-bin/">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature Off

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

---

### Post by charlier653 on 2007-07-25
ok, i think i'm getting it.

still having a bit of trouble getting things copied into /home/*/apache2/htdocs

i can copy individual items, but can't seem to get folders to copy. keep getting this error: cp: omitting directory `/media/cdrom/htdocs/unedited/'

any idea why i can't just copy the folder and contents? or am i missing an operand?

hmmm....just tried cp -R, and it seemed to work.

now to find all th conf files i need to change

---

### Post by chrisf79 on 2007-07-25
if you copy it to CDROM, try sudo cp /cdrom /var/www/yourdirectory and see if that works.  The /var/www is owned by root usually so that might be why you're having troubles.

---

### Post by DBStevens on 2007-07-25
Ah yes, but why did you use the command line to do what is a copy paste in the gui?

---

### Post by charlier653 on 2007-07-25
when i tried to use the gui c/p, i got nothing. i try to copy, and get the message " will copy when pasted". I navigate to the destination, but no paste, just grey section where paste is in right click menu

going to give it up for tonight......work more on it in the AM

thanks!!

---

### Post by trak87 on 2007-07-25
You need to use "sudo" whenever you copy a file anywhere outside of your home directory, otherwise you get permission errors. Thus, you'd do something like this:

```
sudo cp source destination
```

or if you want to copy recursively (current directory and below), something like this:

```
sudo cp -a /media/windows_c/htdocs /var/www
```

---

### Post by charlier653 on 2007-07-26
got it, thanks!

now i need to find all the files that need to be changed from the install default to my website.

apache may install easier under windows, but in so doing, the website admin most likely won't know how to fix it if the install breaks.......yes, i'm looking in the mirror right now....:lolflag:

anyway, i'll get it figured out somehow. probably need to do a lot of reading!!!

---

### Post by rich.bradshaw on 2007-07-26
Apache is easier to install in linux, but it's just about knowing about permissions.

To be more secure, /var/www is not owned by you, it's owned by www-users. This means that nothing can modify these files apart from people with root credentials or apache or php. It's like having a maximum security room where only some people have clearance.

This means that if something goes wrong with your website, noone can edit these files.
 If your php gets 'hacked' then the only files they can edit are these ones, not the rest of your PC.

Basically, this makes everything a lot more secure and is one of the main differences between Windows and Linux.

---

### Post by DBStevens on 2007-07-26
Apache is easiest to setup for multiple websites under a system such as WHM but that in and of itself leads to other issues.

I haven't really looked at who owns what in the Ubuntu take on Apache it is possible to have each site use only the credentials of its user which is much tighter than being a member of a group that has access.

Yep on the permissions, that is a huge change from a wide open free for all.

charlier653, one of these days I'll install the GNOME side of things to see the c/p situation in the GUI. 

Good luck

---

### Post by charlier653 on 2007-07-26
Ok, thanks!

Got the main page working finally, and came up with a different problem.

Now, when I try to navigate through the [site]("http://jens-home-renovation.no-ip.info"), all of my thumbnails show as broken links, but when you click on the broken images, the actual full sized image shows up as it is supposed to.

Is there anyone here familiar with this type of problem? I.E. what coding changes do I need to make?

OOPS!

Found the problem and am fixing it!!

Thanks to you all for helping me get it up and running again!

---

### Post by charlier653 on 2007-07-28
Hmmmm....

Thought I had it fixed, but the problem has returned. 

I don't know if it is a problem with my HTML or ???

I'll see if I can find anything in a more appropriate forum elsewere on the web.

---

### Post by DBStevens on 2007-07-28
Looks to me like you haven't always got the pics where you specified in the html  a large number are working.

Details will nail you everytime ;-).

You'll have a PM shortly.

---

### Post by charlier653 on 2007-07-28
Ok, 

Checked, double checked, and triple checked to make sure all links pointed to actual objects (pictures, html)

Made sure all objects are where they are supposed to be. 

No change to how the website displays. At wits end here.

Why won't it work right?????](*,)](*,)](*,)](*,)](*,)

---

### Post by DBStevens on 2007-07-28
Ya know charlier, I get paid good money for playing with web sites.

You are on a Linux server now and everything about the Linux filesystem applys and the first difference is that Linux is case sensitve.

On your kitchen page you have this for one of the links: 

[http://jens-home-renovation.no-ip.info/kitchen/kit080.jpg](http://jens-home-renovation.no-ip.info/kitchen/kit080.jpg)

however in the directory for that part of your site you have:

[http://jens-home-renovation.no-ip.info/kitchen/kit080.JPG](http://jens-home-renovation.no-ip.info/kitchen/kit080.JPG)

Them's not the same ;-).

You also have an information leak your server is producing a directory listing on the web.  Under a lot of conditions this can cause lots of trouble.

[http://jens-home-renovation.no-ip.info/kitchen/](http://jens-home-renovation.no-ip.info/kitchen/)

---

### Post by charlier653 on 2007-07-28
DB,

I Thank you profusely for your help. 

The case sensitivity appears to be the problem, and I am working on fixing that.

Thanks!!

C

PS: I guess this is another example of being used to a different OS................live and learn!!

---

