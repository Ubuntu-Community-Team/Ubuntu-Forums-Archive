---
title: "Apache2 and PHP5: 'What should Firefox do with this file' problem"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by gordonsowner on 2007-09-13
Hi,

I cannot get Apache2 to serve up .php files.  I get the error on the subject line, with firefox thinking that it has to download the file, not render it.

i have done the following:

```

sudo apt-get install apache2 libapache2-mod-php5
# below installed missing packages
sudo apt-get -f install
sudo a2enmod php5

```

the error after the last command was:

This module does not exist!

Also, after looking through other threads, I have the following facts that seem relevant:

[LIST=1]
[*]There are no lines in apache2.com that even talk about PHP
[*]I don't have a /etc/apache2/mods-enabled/php5.conf
[/LIST]

Can anybody help me here?

Thanks!

---

### Post by bwhitaker on 2007-09-13
sudo apt-get install php5
?

---

### Post by bikeboy on 2007-09-13
> **gordonsowner said:**
> 
[LIST=1]
[*]There are no lines in apache2.com that even talk about PHP
[*]I don't have a /etc/apache2/mods-enabled/php5.conf
[/LIST]


Can you list what's in /etc/apache2/mods-available for us?

```
ls -l /etc/apache2/mods-available
```

The only reference to php in my apache2.conf is part of DirectoryIndex.."index.php" is part of that line.

---

### Post by gordonsowner on 2007-09-13
OK, thanks... further update.

I tried fresh and installed according to:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_PHP_for_Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_PHP_for_Apache_HTTP_Server)

Results:
Apache2 works.
php5.* files are now shown in /etc/apache2/mods-enabled

however,

[http://localhost](http://localhost) resolves to a page that has a header 'Placeholder page' and more stuff.  That's cool.

However, when I try to access:

[http://localhost/apache2-default/index.html](http://localhost/apache2-default/index.html)

I get an 'Unable to connect' error.  index.html does exist in:

/var/www/apache2-default

i chmod'ed all files in here to 755.

oddly, i cannot find the actual file on my system has the text 'Placeholder page' in it.

Am I making progress?

Oh, and can you tell me if/where in apache2.conf i can find that Apache is pointing at the /var/www directory for served files?

=== OK, I got it working.

For some reason, I have no 'httpd.conf' file.  So, I added the following lines to apache2.conf:

> #mtp:xxx
#Include /etc/apache2/httpd.conf

#mtp changes
DocumentRoot "/var/www"

<Directory />
    Options FollowSymLinks
    AllowOverride None
    Order deny,allow
    Deny from all
</Directory>

<Directory "/var/www">
    #
    # Possible values for the Options directive are "None", "All",
    # or any combination of:
    #   Indexes Includes FollowSymLinks SymLinksifOwnerMatch ExecCGI MultiViews
    #
    # Note that "MultiViews" must be named *explicitly* --- "Options All"
    # doesn't give it to you.
    #
    # The Options directive is both complicated and important.  Please see
    # [http://httpd.apache.org/docs/2.2/mod/core.html#options](http://httpd.apache.org/docs/2.2/mod/core.html#options)
    # for more information.
    #
    Options Indexes FollowSymLinks

    #
    # AllowOverride controls what directives may be placed in .htaccess files.
    # It can be "All", "None", or any combination of the keywords:
    #   Options FileInfo AuthConfig Limit
    #
    AllowOverride None

    #
    # Controls who can get stuff from this server.
    #
    Order allow,deny
    Allow from all

</Directory>

<IfModule dir_module>
    DirectoryIndex index.html
</IfModule>

#mtp: end changes

Now it works.  I don't know if it is all necessary, but it is sufficient.

---

### Post by bikeboy on 2007-09-14
Apache2 uses the "sites-available" and "sites-enabled" folders for configuring your sites. I have an httpd.conf but there are only three commented out lines in there. I'm not expert though, so I can't comment on your additions. As long as it works :)

---

### Post by louieb on 2007-09-14
```
sudo tasksel install lamp-server
```[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Setup lamp worked for me. [Lou's Home Server Stuff]("http://louieb.isa-geek.net/")
Up and running on this PC.

---

### Post by hyper_ch on 2007-09-14
MySQL:  [http://www.howtoforge.com/perfect_setup_ubuntu704_p4](http://www.howtoforge.com/perfect_setup_ubuntu704_p4)
Apache2/PHP5: [http://www.howtoforge.com/perfect_setup_ubuntu704_p6](http://www.howtoforge.com/perfect_setup_ubuntu704_p6)

---

### Post by gordonsowner on 2007-09-14
Hi All,

Thanks -- I found that I did not have a DocumentRoot set in apache2.conf (nor http.conf, as the file didn't exist).  I set it with the /var/www directory as root and restarted apache2.

I figured this out by surfing around for someone else's http.conf file, and found that section where they specified the document root.

thanks y'all for your help -- much appreciated.

---

