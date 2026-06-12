---
title: "apache password"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by verbatim210 on 2006-06-20
just incase neone is trying to set up apache in ubuntu, i spent (or should i say wasted) a few hours on this problem and it the end... it was something so simple.

most guides refer to httpd.conf >> use apache2.conf instead

and if u want to password protect ur webpages...  cut paste and edit this into apache2.conf

<Directory "/var/www/*directory name*">
        AuthType Basic
        AuthUserFile *directory of the htpasswd file*
        AuthName "blah blah blah"
        require valid-user *username*
</Directory>

---

### Post by simone.brunozzi on 2006-06-20
Verbatim,
apache2 is a complex software, exposed to public access... I suggest everybody to carefully read the manuals and howtos, to be sure that it is installed and configured properly.
Linux is non strictly secure by default: some tuning is still necessary!

Cheers,

---

### Post by henriquemaia on 2006-06-20
[quote=verbatim210]just incase neone is trying to set up apache in ubuntu, i spent (or should i say wasted) a few hours on this problem and it the end... it was something so simple.

most guides refer to httpd.conf >> use apache2.conf instead

and if u want to password protect ur webpages...  cut paste and edit this into apache2.conf

<Directory "/var/www/*directory name*">
        AuthType Basic
        AuthUserFile *directory of the htpasswd file*
        AuthName "blah blah blah"
        require valid-user *username*
</Directory>[/quote] 
Hi Verbatim, 

Thanks for posting this information. 

Just a small note:

httpd.conf is also present on Ubuntu installation. As such, you can place the password protection directive in it, as it will keep things tidy on apache2.conf.

My httpd.conf looks like this:

# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

<Directory /path/to/the/folder/to/protect>
    AuthType Basic
    AuthName "You can write here whatever you want. This is what will be shown on the password request dialog "
    AuthUserFile /path/to/the/passwords/file
    Require valid-user
</Directory>

________


For others reading this: to use this directive to password protect a folder, you have to create the passwords file. For that you have to use the command

** htpasswd -c passwordfile username**

to create (-c) a new user. 

Example:
```
sudo htpasswd -c /etc/apache2/photos_passwords henriquemaia
``` 
You will  be then asked for the password for the selected user. The password will be store encryped on the file you chose.

If you want to add new users to access that folder, you use the command

** htpasswd passwordfile username**

this time without the -c option.

Example:
```
sudo htpasswd /etc/apache2/photos_passwords other_user
``` 

Also, remember that this line

** AuthUserFile /path/to/the/passwords/file**

on the password protection directive on httpd.conf should point to where you have the passwords file stored.

---

### Post by dchurch24 on 2008-03-04
Hi all - thanks for the information.

Is there something missing though?  I have done as the above has stated (and even tried other methods from other sites) but when I go to that web diectory, it just loads the page. No password protection at all.

I have this:
```

<Directory "/usr/www/wiki">
        AuthType Basic
        AuthUserFile "/usr/local/wiki/.htpasswd"
        AuthName EnterPassword
        require dave
</Directory>

```
in apache2.conf

I have this:

```

AllowOverride All
AuthUserFile /usr/local/wiki/.htpasswd
AuthName EnterPassword
AuthType Basic

require user dave

```

in .htaccess in the usr/www/wiki folder.

for some reason though, it's still ignoring it - or seeminly ignoring it.

Any suggestions as to what I might be doing wrong?

I have been restarting Apache after every change (even though I assume this is overkill).

Thanks in advance.

---

### Post by Oldsoldier2003 on 2008-03-04
> **dchurch24 said:**
> Hi all - thanks for the information.

Is there something missing though?  I have done as the above has stated (and even tried other methods from other sites) but when I go to that web diectory, it just loads the page. No password protection at all.

I have this:
```

<Directory "/usr/www/wiki">
        AuthType Basic
        AuthUserFile "/usr/local/wiki/.htpasswd"
        AuthName EnterPassword
        require dave
</Directory>

```
in apache2.conf

I have this:

```

AllowOverride All
AuthUserFile /usr/local/wiki/.htpasswd
AuthName EnterPassword
AuthType Basic

require user dave

```

in .htaccess in the usr/www/wiki folder.

for some reason though, it's still ignoring it - or seeminly ignoring it.

Any suggestions as to what I might be doing wrong?

I have been restarting Apache after every change (even though I assume this is overkill).

Thanks in advance.

first make dave a apache username and password
```
sudo htpasswd -c /usr/local/wiki/.htpasswd dave
```

your conf and .htaccess are written wrong, this is the proper way:
```
Require valid-user
```

---

### Post by dchurch24 on 2008-03-04
You are a diamond!!

Thanks for the really fast reply.

I did have a .htpasswd file that I created myself. I deleted that, and (hangs head in shame) fixed the path error:

<Directory "/[COLOR="Red"]usr[/COLOR]/www/wiki">  (should be var - duh!)

...and guess what...it works!

Thank you very much!

---

