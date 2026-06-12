---
title: "[SOLVED] Apache2 PHP5 &amp;quot;Opening ______&amp;quot; Problem"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by altonbr on 2006-08-25
Hey guys,

I've learnt (kind of) how to setup an Apache2 and PHP5 server in Windows... and a Apache1.3 server in FC4... but I'm stuck here.

I did the common
```
sudo apt-get install apache2 php5
```
to setup my web server.

[http://localhost](http://localhost) works, so therefore Apache is working... but my files that end in .php are giving my prompts to download them instead of rendering the php... so I can only assume that a line in the apache2.conf is missing or misspelt... but the only lines that contain php are:

```
DirectoryIndex index.html index.php
```
and
```
AddType application/x-httpd-php .php .html
```

by default, the one line was:

```
#AddType application/x-httpd-php .php
#AddType application/x-httpd-php-source .phps
```

but I thought that should be uncommented.. because that's telling Apache when to send the file through php right?

Anyway, I attached a screenshot.

---

### Post by hobbit1983 on 2006-08-25
Do you have the libapache2-mod-php5 package installed.  I have the setup working on my box so I know it's possible - don't remember having your issue.  I will attempt to help all I can though

---

### Post by FuriousLettuce on 2006-08-25
There ought to be two files called 'php5.conf' and 'php5.load' in /etc/apache2/mods-available/, and two symlinks to these files in /etc/apache2/mods-enabled/

If both of these exist, and the AddType lines are uncommented, first make sure that you have restarted Apache since you changed the config file:

```
sudo /etc/init.d/apache2 restart
```

then wipe the cache of your firefox browser (tools -> clear private data IIRC), close firefox then try to reload a php file.

If that doesn't work, do 

```
sudo apt-get remove --purge apache2 php5
```

then reinstall

---

### Post by altonbr on 2006-08-27
As far as I know, I uninstalled then reinstalled and it's still giving me the dialog box. I check for libapache2-mod-php5 and it was installed. I've had this happen on my windows box before and I think it had something to do with a misspelling of this line:

```
AddType application/x-httpd-php .php .html
```

I've attached me current apache2.conf and also my /sites-available/default file to my server for you to view: [http://altonbr.dyndns.org/]("http://altonbr.dyndns.org/")

---

### Post by altonbr on 2006-08-28
Sorry for the bump guys, but does anyone know the answer? :-?

---

### Post by annda on 2006-08-28
everything worked for me after a synaptic install of php5 etc. so i don't know if i can help, but i noticed that i have the php lines still commented out in apache2.conf, but instead present in /etc/apache2/mods-enabled/php5.conf

maybe try searching for php5 in synaptic and install the remaining packages... (just a suggestion, that's what works for me, no idea what logic is behind it.)

---

### Post by altonbr on 2006-08-28
I don't have a /etc/apache2/mods-enabled/php5.conf.. I'm assuming that is it???

I copied php5.conf from mods-available to mods-enabled and it's still not working... I even uninstalled apache2 and php5 and re-installed them.. it does have anything to do with running off a FAT32 partition through fstab does it?

---

### Post by Kilz on 2006-08-28
> **altonbr said:**
> I don't have a /etc/apache2/mods-enabled/php5.conf.. I'm assuming that is it???

I copied php5.conf from mods-available to mods-enabled and it's still not working... I even uninstalled apache2 and php5 and re-installed them.. it does have anything to do with running off a FAT32 partition through fstab does it?

You have also copied the php5.load from mods-avaiable to mods-enabled or made sure its there? Then restarted apache, or rebooted?

---

### Post by az on 2006-08-28
> **altonbr said:**
> I don't have a /etc/apache2/mods-enabled/php5.conf.. I'm assuming that is it???

I copied php5.conf from mods-available to mods-enabled and it's still not working... I even uninstalled apache2 and php5 and re-installed them.. 


To enable an apache2 module, it is easier to use the tools provided:

sudo a2enmod php5

But it should already be enabled if you install libapache2-mod-php5.




Use this as a refercence that is Ubuntu-specific:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)



> **altonbr said:**
> 
it does have anything to do with running off a FAT32 partition through fstab does it?

Probably.  Fat32 partitions do not handle linux file properties and ownerships.  Under what user and group is it mounted?  www-data is the apache2 user that needs to access those files.

---

### Post by altonbr on 2006-08-30
Phew! I was hoping it wasn't my FAT32 partition.. because while I'm in school, I have to do projects using Flash... once I'm done though.. 100% Ubuntu.

So I used

```
sudo a2enmod php5
```

and then reloaded apache

```
sudo /etc/init.d/apache2 force-reload
```

and now it's working... so if you say that should have been included along with 'libapache2-mod-php5' then does anyone have any speculation as to what may have happend?... AND what is 'a2enmod'?

---

### Post by altonbr on 2006-08-30
Oh AND the footer finally says

```
Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at altonbr.dyndns.org Port 80
```

but it left out the PHP last time... so something was definetely up. How do I change that footer anyway? Those are 4 different variables right?

---

