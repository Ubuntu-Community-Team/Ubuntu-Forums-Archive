---
title: "New LAMP install method doesn't respond to CLI commands?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-07-25
I'm used to install LAMP on Desktop this way
```
sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server
```
But I wanted to try a new install method that's more Ubuntu like ever since a did a clean Feisty install.
>    1. Open Synaptic Package Manager
   2. Select "Edit" -> "Mark Packages by Task"
   3. Select "LAMP Server"
   4. Click OK
   5. Click Apply
   6. Wait for Synaptic to download and install the services.

But when doing commands like these it won't respond, know what I'm doing wrong :confused:

> mikey@renaissance:~$ **sudo /usr/sbin/apache2ctl restart**
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
mikey@renaissance:~$ 

---

### Post by DBStevens on 2007-07-25
What is in: 

/etc/hosts 

and

/etc/hostname

and 

/etc/apache2/sites-enabled/000-default

Looks to me like the Apache2 server install went just fine, some other related things need a tweak.

---

### Post by jingo811 on 2007-07-25
> 
What's in:
**/etc/hosts**
```

127.0.0.1	localhost
127.0.1.1	renaissance

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```


> 
What's in:
**/etc/hostname**
```
renaissance
```


> 
What's in:
**/etc/apache2/sites-enabled/000-default**
> 
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
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
	ServerSignature On

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

### Post by DBStevens on 2007-07-25
The 

127.0.1.1 renaissance

line in your /etc/hosts file should read something like
 
127.0.1.1 mymachine.texas.rr.com renaissance

The format for a host file entry is:

IP_address canonical_hostname [aliases...]

[http://linux.die.net/man/5/hosts](http://linux.die.net/man/5/hosts)

BTW that error in and of itself doesn't stop the server from starting.

So you might want to provide the contents of 

/var/log/apache2/error.log

and the output from 

ps -All

---

### Post by jingo811 on 2007-07-26
OK I'm giving up trying to install LAMP the Ubuntu way.  It seems like it involves more work than doing it manually through terminal.  I just thought I'd give it a shot in case it was easier to setup apparently it's not.
So how do you uninstall LAMP the Ubuntu way?  I back traced my previous install process but Synaptic won't let me unselect the ticked LAMP option.  So I can't uninstall it.

> 1. Open Synaptic Package Manager
2. Select "Edit" -> "Mark Packages by Task"
3. Select "LAMP Server"
4. Click OK
5. Click Apply
6. Wait for Synaptic to download and install the services.

How can I uninstall what I've done?

---

### Post by DBStevens on 2007-07-26
Before you go off unhappy why don't you fix the non LAMP issue namely your /etc/host file?

The problem you are seeing isn't a show stopper or even preventing the use of the server. 

If you really expect a default install of LAMP to correct your networking setup you'll be waiting forever plus a day.

As for uninstalling it you'll probably have to remove each component.  Since I've never used that method of installing groups of packages I don't know.

BTW your LAMP install did respond to CLI commands.

---

### Post by jingo811 on 2007-07-26
How can I find the list for each component that got installed the Ubuntu way?
Since I'm no longer allowed to deselect nor select that option I can't see all the respective components anymore.  And I remember the list for those components were 3 times as long compared to installing LAMP the CLI way.

```
sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server
```

I want to test this method instead which worked when I used Dapper Drake.  And see if I get the same error problem.

---

### Post by jingo811 on 2007-07-26
Regarding your tip.
> line in your /etc/hosts file should read something like

127.0.1.1 mymachine.texas.rr.com renaissance

Should I put this in my /etc/hosts file then?  I only use it to develop webdesigns and I don't understand the text in that manual you linked, it's too technical for me :-(
```
127.0.1.1 localhost renaissance
```


.......OK now it seems I don't get any error when restarting Apache I copied your line straight off  
> 127.0.1.1 mymachine.texas.rr.com renaissance
But I don't understand the **mymachine.texas.rr.com** part, can I just fake the domain name however I want doesn't it have to be something real :confused:

---

### Post by DBStevens on 2007-07-26
You didn't read the information at the link I provided did you, you were also thinking that the meassge you got when you ran the CLI command actually prevented the server from starting it doesn't on my system when I get it and I don't think it did on your system but in case it did I asked you to provide the messages in the servers error log and a list of all processes running on your system.

I didn't try it with 127.0.1.1 localhost localhost, it may or may not get rid of the message, you can try it.  I provided an example of a valid canonical hostname, I didn't say it would be the same for you.  But since 127.0.1.1 is local to your system probably can get away with any properly formatted name.

---

### Post by DBStevens on 2007-07-26
I do a bit of webdesign work as well which is why I have Apache on my home system.  I use it as a testing platform before pushing changes to a test server.

It prevents most blunders from escaping ;-).

If haven't looked at the meta package that Synaptic used for the install method you used so I really don't know what it installed, however if you know the packages it actually installed you can back them out by using the individual package removal facility.

---

### Post by jingo811 on 2007-07-26
mmm... as long as it all works and I can stick to my pre-made configurations to-do list.  Then I probably sholdn't break what's not broken.

However I read that /etc/hosts link one more time
[http://linux.die.net/man/5/hosts](http://linux.die.net/man/5/hosts)
Yet I still don't understand the reason for that file and what that manual is trying to say :confused:
So far I understand that for each ip you need to connect a hostname. 
> Example

127.0.0.1       localhost
192.168.1.10    foo.mydomain.org    foo
192.168.1.13    bar.mydomain.org    bar
146.82.138.7    master.debian.org      master
209.237.226.90  [www.opensource.org](www.opensource.org)

But if there's 2 different PC's in the world developing on Apache and they both point the same hostname to the same ip for instance 192.168.1.10 won't their be any conflicts for visitors?
And if the hostname Ubuntu.org doesn't belong to me aren't I causing trouble with the Ubuntu.org owners then?
Maybe I'm asking the wrong questions since I don't understand the reason for** /etc/hosts**

That's why I wanted to undo the pre-packaged LAMP and install it with my old CLI method.  Because back then I didn't have to know about or concern myself with the /etc/hosts file.

---

### Post by DBStevens on 2007-07-26
In order for a domain name to be on the internet it has to be in a domain nameserver that is pointed to by the registration provider.  It is in the domain nameserver that a name is pointed to a physical address.

In short what you do locally on your machine has no effect on the rest of the internet.

Apache is just being picky it wants a valid name to use, normally it would be mydomainname.something which you would have registered and had provided pointers to a Domain Name Server for.  The DNS would point to the address of the server the site was on.  Then the server would use the name to look up what hopefully is a valid server alias in order to provide the proper directories to serve the requested pages from.

I think you are confusing what happens when Ubuntu installs the server software.  I installed my LAMP stack by installing each package, the first time I started the server I got the very same message you did.

However, I checked to see if the server actually was running and it was.  Then I changed my /etc/hosts file, I didn't have to but I did.

---

### Post by jingo811 on 2007-07-26
Tnx for the explanation.
I sure hope that Synaptic will update the LAMP package for me as soon as possible and not after 3 months, whenever there's a major critical update for either Apache, MySQL or PHP.
Coz there's no undoing this Ubuntu way installation not by simply clicking things anyway.

---

### Post by az on 2007-07-26
> **jingo811 said:**
> Tnx for the explanation.
I sure hope that Synaptic will update the LAMP package for me as soon as possible and not after 3 months, whenever there's a major critical update for either Apache, MySQL or PHP.
Coz there's no undoing this Ubuntu way installation not by simply clicking things anyway.

Just keep up-to-date with security upgrades.


sudo apt-get dist-upgrade


When a new release is out, run

sudo do-release-upgrade
(I have to confirm that update-manager-core is installed by default...)

---

### Post by jingo811 on 2007-07-26
tnx.

---

