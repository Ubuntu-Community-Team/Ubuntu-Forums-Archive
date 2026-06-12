---
title: "HOWTO FTP files from Windows 2000 laptop to Ubuntu server"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by guitarman on 2007-12-30
Hi All,

sorry for the silly question, but I just set up my Ubuntu web server, configured apache and the test page come up fine.  I also installed vsftp and openssh and I am able to SSH into the server with no problem.  Using my Windows 2000 laptop I am able to copy files from the Ubuntu server to my laptop using SimpleFTP client, but I cannot send files from my laptop to the Ubuntu server. I have 3 small files for a web site that I want to host on the Apache, but cannot for the life of me upload them to the server.  I keep getting a Transfer failed error in the Easy FTP client.

Does anyone know what I am doing wrong or is there an easy way of transferring these files.  If I should use VSFTP what would be the command line and where do I type it (in the telnet session of putty or in the cmd session of Windows).

Thanks for the help...

Both server and laptop are on my internal home network and I can ping both from one another.

---

### Post by ^rooker on 2007-12-30
vsftpd is fine, but if all you want to do is simply upload files every now and then to your linux machine without bothering about configuring the FTP server, use sFTP (it's FTP over SSH).

A nice (excellent) client for that (and FTP in general) is "FileZilla": [http://filezilla-project.org/]("http://filezilla-project.org/")
(the client)

Just use your linux username/password and select "FTP over SSH" as protocol - and you'll immediately be able to upload/download files to your home directory.

---

### Post by guitarman on 2007-12-31
Thanks ^rooker,
this seemed to work fine.  I went back to use SimpleFTP and noticed that it was failing because I was trying to upload the files directly into the /var/www directory and not into my /home directory.  When I changed this, I was able to upload with both Filezilla and SimpleFTP.  I later copied the 3 files into the /var/www as well as /var/www/mywebsite.com directories.  However, now when I run my browser and point it to the apache web server it tells me:
---------------------------
(Forbidden
You don't have permission to access /index.html on this server.  )
----------------------------

It worked fine with the simple index.html (Hello file) that I created initially.  I overwrote this file with my actual web site page.

I also tried to restart apache and it gave me this:
===================================
sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                                   apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Mon Dec 31 00:02:43 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Mon Dec 31 00:02:45 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
                                                                         [ ok ]
====================================

the mysite.com file located in the /etc/apache2/sites-enabled directory did not change from when I created it with the initial test index.html file; do I need to make any other change?

thanks again,

---

### Post by ^rooker on 2007-12-31
Of course, you can only upload files to directories that you have write access to. ;)

I'm not sure if I understood you correctly:
Did you locate your website's files in /etc/apache2/sites-enabled? If so, you've made a mistake, because the website's files (e.g. index.html) go into subdirectories of /var/www (or directly into /var/www if you only have 1 site).

Everything in /etc is for configuration *only* - no content.
(/etc/apache2/sites-enabled should contain only symlinks to the config files in /etc/apache2/sites-available and are for configuring different sites/virtual hosts)

If you're unfamiliar with configuring apache, I'd highly recommend that you read some tutorials (Just google for "HowTo apache").


However, for convenience, you could change the permissions of e.g. /var/www/ so that your user is allowed to upload files there directly.

--EDIT: Sorry, I've overlooked that you've mentioned that you've already put your files in /var/www. The error messages indicate 
a) That you haven't configured your apache and/or your hostname properly. It seems to bind only to localhost, so you either got to configure the "Listen" setting correctly (e.g. Listen 192.168.1.1:80) or your <VirtualHost/> section, depending on your setup. I can't give you details here without knowing your configuration.
b) The access thing is also: either apache configured to lock you out, but usually the website's files are not readable by the user "www-data". Check that first.

---

### Post by guitarman on 2007-12-31
Here is my file.  Please let me know what I need to add/remove to make it work.  Thanks and Happy New Year.
============================

NameVirtualHost *
Listen 192.168.1.10:80
<VirtualHost *>
        ServerAdmin [email]myemail@yahoo.com[/email]
        ServerName mywebsite.com
        ServerAlias [www.mywebsite.com](www.mywebsite.com)
        DocumentRoot /var/www/mywebsite.com
        <Directory />
        Options FollowSymLinks
        AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
 AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
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
==========================================

---

