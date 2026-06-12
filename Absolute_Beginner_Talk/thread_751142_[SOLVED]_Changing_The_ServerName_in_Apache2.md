---
title: "[SOLVED] Changing The ServerName in Apache2"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by KMuchane on 2008-04-10
Hello...,

I am trying to configure Apache2.2 which I installed the other day.
My problem is not that complex...or so I thought.I want to change the ServerName to something more appropriate but apparently I cannot...but first things first. Here are the contents of the /etc/apache2/htttpd.conf which I edited:

NameVirtualHost 127.0.0.1

<VirtualHost 127.0.0.1>
        ServerName [www.kinuthia.com](www.kinuthia.com)
        ServerAlias kinuthia.com
        ServerAdmin [email]webmaster@kinuthia.com[/email]
        DocumentRoot /home/kinuthia/www/

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

        <Directory /home/kinuthia/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>


When I restart the sever through /etc/init.d/apache2 restart, I am helpfully reminded that:
* Restarting web server apache2     
        apache2: apr_sockaddr_info_get() failed for tchane
        apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
        
                                                                                 [ OK ]
        'tchane' is the computer's hostname.

So, every time  I try to access the files in the DocumentRoot I have to type in 127.0.0.1. How do I get round this?
Someone to the rescue?
Thanks!

---

### Post by mmc on 2008-04-12
what name are you wanting to use to access you apache virtual host?  

I'm guessing (from reading between the lines) what you actually want is name based hosting (so for an immediate fix look to change the contents of the ViritualHost tag to be something like:  <VirtualHost www.mysite.com>   .... & if your just testing locally then adding the [www.mysite.com](www.mysite.com) to your local /etc/hosts file will cause your local browser to find the site.


for full details on name based hosting look here -> [http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html)

hope this helps.

mmc.


p.s. the 'tchane' name resolution warning will be coming from the 'ServerName' directive defined in your main httpd.conf / apache2.conf

---

### Post by KMuchane on 2008-04-13
mmc,
Hello...

Lahaula! Where did the other replies I added disappear to ? Anyway, I have edited, re-edited the /etc/hosts file until I am blue in the face! I have created a file under /etc/apache2/sites-available called kinuthia_site. To enable it I create a soft link to /etc/apache2/sites-enabled with the command sudo a2ensite /etc/apache2/sites-available/kinuthia_site. The contents of that file are:

NameVirtualHost 127.0.0.1

<VirtualHost 127.0.0.1>
	ServerName [www.kinuthia.com](www.kinuthia.com)
	ServerAlias kinuthia.com
	ServerAdmin [email]webmaster@kinuthia.com[/email]
	DocumentRoot /home/kinuthia/www/

	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>

	<Directory /home/kinuthia/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
</VirtualHost>

When I restart Apache2, I get the following message:

apache2: apr_sockaddr_info_get() failed for tchane
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

Incase you ask, I used the same configurations in /etc/apache2/httpd.conf and got the same results! I simply cannot changed the ServerName. I am using this to do some local tesing, so I am not serving any web pages... at least not yet.
There is no where in those configurations where I have used 'tchane', the hostname...

Thanks ...

---

### Post by mmc on 2008-04-13
ok - it sounds as if your confusing IP hosting & namebased hosting, the two don't mix well but let leave that to one side for the moment, essentially if you simply want to have;

[1] web browser look to your own apache install for [www.mysite.com](www.mysite.com)
[2] configure apache to respond based on the name & not the IP (currently 127.0.0.1)

then all you need to do is;

[1] add an alias for [www.mysite.com](www.mysite.com) to 127.0.0.1 in /etc/hosts (then restart browser)
[2] make sure you do not have conflicting 'NameVirtualHost' entries (any other sites-availble


so, the logic flows:
+ one statement saying `NameVirtualHost 127.0.0.1` usually this is centrally held but check your /etc/apache2/sites-enabled/000-default as it may have a catch all
+ every virtualhost uses `<VirtualHost 127.0.0.1>`
+ each `Servername` is a unique name
+ each `Servername` has a corresponding entry in /etc/host like so:
[INDENT]127.0.0.1  [www.mysite.com](www.mysite.com)[/INDENT]

hope this helps.

-mmc

p.s. if you still struggle please post me the outputs of; 
cat /etc/hosts
ls -l /etc/apache2/sites-enabled
[INDENT]& then a 'cat' of each site config listed in sites-enabled[/INDENT]


p.p.s. you are restarting apache after config changes right? ;)

---

### Post by KMuchane on 2008-04-13
mmc,

First I would like to thank you for trying to get me out of the rut!

1) cat /etc/hosts reveals:

127.0.0.1 [www.kinuthia.com](www.kinuthia.com)
# The following lines are desirable for IPv6 capable hosts
#::1 ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts
2) cat ls -l /etc/apache2/sites-enabled shows:

lrwxrwxrwx 1 root root 42 2008-04-11 09:17 kinuthia_site -> /etc/apache2/sites-available/kinuthia_site

I disabled default, so /etc/apache2/sites-available/kinuthia_site is the only file in sites-enabled.

3) cat /etc/apache2/sites-available/kinuthia_site produces:



<VirtualHost www.kinuthia.com>
	ServerName [www.kinuthia.com](www.kinuthia.com)
	ServerAlias kinuthia.com
	ServerAdmin [email]webmaster@kinuthia.com[/email]
	DocumentRoot /home/kinuthia/www/

	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>

	<Directory /home/kinuthia/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
</VirtualHost>

4) There is this line under Using Named-based Virtual Hosts in the Apache2 documentation which says and I quote

'''The next step is to create a <VirtualHost> block for each different host that you would like to serve. The argument to the <VirtualHost> directive should be the same as the argument to the NameVirtualHost directive (ie, an IP address, or * for all addresses). Inside each <VirtualHost> block, you will need at minimum a ServerName directive to designate which host is served and a DocumentRoot  directive to show where in the filesystem the content for that host lives.
'''
Despite those changes the error  '''* Restarting web server apache2
apache2: apr_sockaddr_info_get() failed for tchane
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName ''' persists!

:confused: in a big way!

And of course I am RESTARTING the server after every change!
Lahaula! This boggles the mind...

Thanks!

---

### Post by mmc on 2008-04-13
ok, so stepping through the logic i listed earlier your not quite there yet, remember:

<snip>
so, the logic flows:
+ one statement saying `NameVirtualHost 127.0.0.1` usually this is centrally held but check your /etc/apache2/sites-enabled/000-default as it may have a catch all
+ every virtualhost uses `<VirtualHost 127.0.0.1>`
+ each `Servername` is a unique name
+ each `Servername` has a corresponding entry in /etc/host
</snip>


# NameVirtualHost
unless you have added this to your central apache2.conf then it seems you are missing this, so within your single vhost file (/etc/apache2/sites-available/kinuthia_site) at the top add 'NameVirtualHost *'  [don't include the quotes - same goes for entries below ;) ]

# VirtualHost
change it to match the name virtualhost so it looks like: `<VirtualHost *>`    (you were almost there having found the apache docs, what you found there is true, the contents of nameVirtualHost and virtualHost must be the same, using the wildcard '*' will simplify it and just catch all as opposed to a specific IP (for local testing this is quite ok) ... the core issue so far is that you have removed the nameVirtualHost statement so apache doesn't know its supposed to be using name based hosting.)

# /etc/hosts
what you have _should_ function but i would re-add your local workstation name, you can  have multiple names per single IP, so something having a line like this should do the trick:
  127.0.0.1       localhost tchane [www.kinuthia.com](www.kinuthia.com)


# startup error:
i think you'll find this is simply a warning & not terminal to the startup process. the error is almost certainly coming from the global ServerName (i.e. not in your v.host config) directive in your apache2.conf which is usually set to the local hostname, in your case 'tchane', however you have removed this from the /etc/hosts files & it then cannot resolve its own name. & as i said it will just be a warning and not a critical error. check your apache2.conf to confirm.



let me know how it goes...

-mmc

---

### Post by spiderbatdad on 2008-04-13
In sites-available:

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin your@email.net
        ServerName yourname.com
<Directory />
		Options None
		AllowOverride None
                Order deny,allow
                Deny from all
            </Directory>
         <Directory /home/linux/public_html>
ADD your option etc, for this directory
```

In httpd.conf

ServerName Yourname.com

if you have not established a name through a DNS service, put your ip address there.
[www.whatismyip.com](www.whatismyip.com) should show you, if you dont know for sure.  Same goes vor vitual hosts file.

---

### Post by KMuchane on 2008-04-13
mmc, 

Thanks very much for your enlightening answers. I do not know what I could have done without you... 

It worked... but before   I could sigh with relief, I was denied access! I thought the first Directory container above was for denying Apache access to the root file and the second one  grants access to a particular folder in this case /home/kinuthia/www. 
" You do not have access to / on this server "  and the error code 403 is what I get when I enter [www.kinuthia.com](www.kinuthia.com) in the browser. 
chmod 0777  -R /home/kinuthia/www does not seem to help... 
I hope you will not mind giving me more directions... 

 Thanks!

---

### Post by KMuchane on 2008-04-13
mmc, 

Thanks very much for your enlightening answers. I do not know what I could have done without you... 

It worked... but before   I could sigh with relief, I was denied access! I thought the first Directory container above was for denying Apache access to the root file and the second one  grants access to a particular folder in this case /home/kinuthia/www. 
" You do not have access to / on this server "  and the error code 403 is what I get when I enter [www.kinuthia.com](www.kinuthia.com) in the browser. 
chmod 0777  -R /home/kinuthia/www does not seem to help... 
I hope you will not mind giving me more directions... 

 Thanks!

---

### Post by mmc on 2008-04-13
no problem - glad to hear its starting to work for you :)

the permission denied error will be literal & will almost certainly be file system permissions (parent dir permisson of your users homedir is my best guess - explaination below ;) )

i note that your DocumentRoot is (was? can you re-post your v.host conf file if its changed?) under your home dir. most likely a parent directory permission is not allowing the user running your apache access.

+ to find out who own the web server processes do:
# egrep  '^User|^Group' /etc/apache2/apache2.conf  (should be www-data & www-data)
# ps -ef | grep apache  
[INDENT]the ps output should confirm whats in your conf file[/INDENT]

+ to check the permissons on the directories do;
# ls -ld /home /home/kinuthia /home/kinuthia/www
[INDENT]if any parent dir (most likely it /home/kinuthia) is restrictive to the www-data user then it explains your error. but i suggest you tweak the config as per below[/INDENT]


ok, first up i would strongly urge that you REMOVE the 777 permissons! if you don't know what they were before then recursively chmod'ing to 755 is a relatively safe starting point that shouldn't hinder access too much. Basically allowing world writable files is not a great idea in any scenario & this is especially true for web applications where access tends to be wider than just you.

what i would do is create a sub directory in /var/www/ ... something like /var/www/kinuthia & point your DocumentRoot at it. the files need not be owned by www-data just be readable (via group or world permissions). doing this will allow you to own the files as your application user but still grant the web server processes access to your files

make sense?

let me know how it goes.....

-mmc

---

### Post by KMuchane on 2008-04-14
mmc,
Hi,
:(
This is getting interesting. I transferred the DocumentRoot to /var/www/kinuthia_site as you suggested but "You don't have permission to access / on this server." error continues. I have granted permissions to read that Directory to all by sudo chmod ugo+r  -R  /var/www/kinuthia_site. ls -ld confirms that  drwxr-xr-x 2 root root 4096 2008-04-14 08:21 /var/www/kinuthia_site.

So what could be breaking the link ? :confused:
Thanks buddy!

---

### Post by mmc on 2008-04-14
ok. can you post the contents of your vhost file, the outputs of

# ls -ld /var /var/www /var/www/kinuthia_site
# ls -l /var/www/kinuthia_site

& the relevant entries in the apache error log  (unless you've changed it it will most likely be - /var/log/apache2/error.log )

with the above info we should be able to see the problem & get you past it  ;)

-mmc

---

### Post by KMuchane on 2008-04-14
mmc,  

[...sigh ...] Phew!  I took it  sloooowly and now it is working, I even threw in some php scripts and it parsed them effortlessy ! This has been a learning experience both in programming and in humanity to others. You will never know how grateful I am, buddy. Thank you...

---

### Post by mmc on 2008-04-14
your welcome!  glad to hear its all working for you now - good luck.

-mmc

---

