---
title: "Mediawiki :: Not sure how to back it up??? (dapper)"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by wantime on 2007-02-08
Hi,

Does anyone know how to back up all the mediawiki pages?  I'm trying to administer a small wiki and want to back the whole wiki up to an external disk for reinstallation on another machine.  I've copied all the /usr/share/mediawiki directory but am unsure which files are acutally the pages themselves.

Thanks.

---

### Post by ViRMiN on 2007-02-15
I run a few MediaWiki installations on FC6 systems (I built an Edgy system yesterday hence me registering today on the forum :) )

The pages themselves are contained in a database.  On my FC6 machines, it's MySQL, and can be dumped to a .sql file using mysqldump, see [http://dev.mysql.com/doc/refman/5.0/en/mysqldump.html](http://dev.mysql.com/doc/refman/5.0/en/mysqldump.html) for usage.  You'll need to set-up an database user with the appropriate rights, or use the "root" database user account?  I created a specific account so that I could automate the database SQL save.

You'll also need to save your uploaded files, which are in /var/www/mediawiki/images on a standard FC6 installation.  To be safe, backup the entire mediawiki directory as then you'll get your configuration settings, as well as any extensions you may have installed.

Once on your new box, you can use your .sql file as the input to mysql to create and fill the database.

I hope this gets you heading in the right direction.  I've yet to install MediaWiki on Ubuntu, hence not giving you a very detailed reply!

---

### Post by wantime on 2007-02-15
Great.  Thanks ViRMiN.  I still haven't set up the new wiki, I got distracted tweeking some other aspects of my system since the upgrade.  

I think this was a useful start last time:

[http://meta.wikimedia.org/wiki/Help:Running_MediaWiki_on_Ubuntu_GNU/Linux]("http://meta.wikimedia.org/wiki/Help:Running_MediaWiki_on_Ubuntu_GNU/Linux")

Just make sure to get the latest version, mediawiki 1.4 was badly supported before .. it never upgraded.

I got apache2, php5, mysql and then mediawiki from:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")

Let me know how it goes.

---

### Post by ViRMiN on 2007-02-15
You're welcome!

To be honest, I'll need at least the same version on Ubuntu as I've got on FC6, i.e. 1.8.3, might even manually install and configure 1.9.2.

Shouldn't take me too long to get into Ubuntu.  My MediaWiki's on FC6 are available only over HTTPS connections and are firewalled to allow specific IP's to connect, and then you needed to log-in to see any content!  And, even if you nicked off with my database or a backup of it, it's encrypted too!  Belts and braces!

---

### Post by ViRMiN on 2007-02-15
Okay, I've installed Apache v2, PHP 5, MySQL 5 from the repos, and installed MediaWiki v1.9.2 from the tarball on the website.  Looks to be working so far, just got to make some changes to the Apache configuration to restrict my wiki to HTTPS connections, and block access to the config directory, install my favourite extensions and then transfer the wiki content into it!  It's 11pm localtime, so I'll save all that for another night, got work in the morning :D

---

### Post by wantime on 2007-02-19
So, back again ... I installed mediawiki1.7 (for edgy) from Synaptic.  I'm still getting my head around these programs though.  What does your apache.conf file look like?  I have a feeling that my security and settings are not so good.

---

### Post by ViRMiN on 2007-02-20
I will make a copy of them tomorrow when I'm next in the office.  They're not from an Ubuntu build, they're on a Fedora Core 6 machine.

I've not made any changes to the configuration on my Ubuntu machine yet.   I updated it yesterday to Fiesty Hurd 4 which has fixed a few niggles I had like my USB headset now works properly with Skype!  I'm getting used to Ubuntu now, like where config files live, etc.  E.g. On FC6 the Apache config files are in /etc/httpd whereas on Ubuntu they're in /etc/apache2

---

### Post by wantime on 2007-02-20
Do you also have an apache.conf file in /etc/mediawiki1.x/ ? I'm using this one for the wiki but am wondering if it is better to just use the one conf file in /etc/apache/.  Otherwise it all seems to be working ok, I'm just a little concerned about the security issues around apache.

---

### Post by ViRMiN on 2007-02-20
I've got an httpd.conf in /etc/httpd/conf and a mediawiki.conf and ssl.conf in /etc/httpd/conf.d - like I said though, it's a Fedora box not Ubuntu :)  I'll grab copies tomorrow and chuck the relevant sections up.

I had a requirement to restrict access to the Wiki and also to use HTTPS over the network, hence making the changes.  The restriction to access the /config directory of the Wiki install was standard with the packaged installation from RPM.

---

### Post by ViRMiN on 2007-02-22
Here's a sample mediawiki aliasing (kept in /etc/httpd/conf.d/mediawiki on [COLOR="Red"]**FC6**[/COLOR]).  This restricts access to some of the subdirectories - some there's no reason for them to be served, it's accessed 'internally' via PHP, or from the command line.

```

Alias /mediawiki /var/www/mediawiki

<Location /mediawiki/config>
    Order deny,allow
    Deny from all
    Allow from 127.0.0.1
    # Allow from .example.com
</Location>

<Location /mediawiki/includes>
    Deny from all
</Location>

<Location /mediawiki/languages>
    Deny from all
</Location>

<Location /mediawiki/maintenance>
    Deny from all
</Location>

<Location /mediawiki/math>
    Deny from all
</Location>

<Location /mediawiki/PPP-keys>
    Deny from all
</Location>

```

In /etc/httpd/conf/httpd.conf, I've got the following to restrict access to the Wiki to certain IP's (basically, a subset of the addresses allowed by the firewall, I've obfuscated the address range btw), it also makes it accessible only via HTTPS connections:

```

<Directory "/var/www/mediawiki">
    Order allow,deny
    # Localhost
    Allow from 127.0.0.1
    # Subnet
    Allow from xxx.xxx.xxx.xxx/24

    SSLRequireSSL
</Directory>

```

As I say, these are from one of my [COLOR="Red"]**FC6**[/COLOR] boxes, so you'll probably have to compare your config files and directory locations, etc., to see where the entries need to go - I've not done anything on my Ubuntu box with Mediawiki other than install it, and populate the database from a SQL export...

Hope this is of use to you :)

---

### Post by ViRMiN on 2007-02-22
BTW - Before anyone shouts at me, I know that the PPP-keys directory should really be outside of the webserver directory structure!

---

### Post by wantime on 2007-02-22
That's great.

 :guitar: 

It gives me a point of reference.

Thanks

---

