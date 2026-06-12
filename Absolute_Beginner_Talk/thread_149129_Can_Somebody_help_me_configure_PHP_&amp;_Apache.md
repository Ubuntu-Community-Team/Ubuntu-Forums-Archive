---
title: "Can Somebody help me configure PHP &amp; Apache?"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-23
Hello !!!

I have tried repeatedly to install & configure the above programs, but with NO luck!!!

MySQL seems to be working fine...

But I can NOT see the Apache's Home Page...

From my Mozilla Firefox, I type:

[http://localhost/var/www/apache2-default](http://localhost/var/www/apache2-default)

And get this output:
Not Found
The requested URL /var/www/apache2-default was not found on this server.
Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 Server at localhost Port 80

Please Help...

Thanks in advance.

---

### Post by LanceM on 2006-03-23
This is the step-by-step that I used and was successful:

[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---

### Post by dvarsam on 2006-03-23
[QUOTE=LanceM]This is the step-by-step that I used and was successful:

[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)[/QUOTE]

I followed it & it did NOT work with me...

I even bought a Book for this & still did not get it to work...

Can Somebody Help?

Please..........

---

### Post by zericm on 2006-03-23
Your webserver appears to be working fine, but the URL you are trying to access is wrong. Try this one: 

[http://localhost/apache2-default/](http://localhost/apache2-default/)

---

### Post by dvarsam on 2006-03-23
[QUOTE=zericm]
Your webserver appears to be working fine...
The URL you are trying to access is wrong!
Try this one: 

[http://localhost/apache2-default/](http://localhost/apache2-default/)[/QUOTE]

Dear "zericm",

You are so awesome man!!!

I couldn't figure out what was wrong... & it was so simple man!!!

Thanks.

P.S.> Right now, my "/var/www" folder contains 3 files/folders:

1. apache2-default     (I think this was installed by default)
2. test.php                 (I created this file)
3. phpmyadmin -> /usr/share/phpmyadmin    (I did not create this)

If I would like to have my Web Pages Posted in there...

Should I delete numbers 1 & 3?

And keep only MY website inside the "/var/www" folder?

OR: is that NOT permitted (or even NOT the common approach)?

Thanks.

---

### Post by dvarsam on 2006-03-23
[QUOTE=dvarsam]
Right now, my "/var/www" folder contains 3 files/folders:

1. apache2-default     (I think this was installed by default)
2. test.php                 (I created this file)
3. phpmyadmin -> /usr/share/phpmyadmin    (I did not create this)

If I would like to have my Web Pages Posted in there...

Should I delete numbers 1 & 3?

And keep only MY website (e.g. test.php), inside the "/var/www" folder?

OR: is that NOT permitted (or NOT even considered a common approach)? [/QUOTE]

Anyone?

---

### Post by indytim on 2006-03-23
dvarsam:

You will need to have your pages for your local Apache instance contained within the root for Apache /www.

Good Luck,

IndyTim

---

### Post by dvarsam on 2006-03-23
[QUOTE=indytim]

You will need to have your pages for your local Apache instance contained within the root for Apache /www.

[/QUOTE]

Well, all the above 3 files are inside the "www" folder - if this is what you mean...

Can I delete the above numbered 1 & 3?

Can you be more specific?

Also, when I visit the "localhost/phpmyadmin", I can NOT log-in...

What is the default username & password to enter into the "phpmyadmin's" settings?

---

### Post by kennethb on 2006-03-24
[QUOTE=dvarsam]Well, all the above 3 files are inside the "www" folder - if this is what you mean...

Can I delete the above numbered 1 & 3?

Can you be more specific?

Also, when I visit the "localhost/phpmyadmin", I can NOT log-in...

What is the default username & password to enter into the "phpmyadmin's" settings?[/QUOTE]

I suggest not removing #1 & #3 above. Try adding a new  directory to the /var/www directory with:

% sudo mkdir /var/www/new_site

Then add an HTML page to this directory. Then open your browser and type the address:

[http://localhost/new_site](http://localhost/new_site)

---

### Post by mlind on 2006-03-24
I suggest you enable usermod (module) and develop web content locally.

```

sudo a2enmod usermod
mkdir ~/public_html

```

then your site is accessible using
[http://localhost/~dvarsam/](http://localhost/~dvarsam/)

Then do your development on ~/public_html directory instead of /var/www

---

### Post by dvarsam on 2006-03-25
[QUOTE=mlind]I suggest you enable usermod (module) and develop web content locally.

```

sudo a2enmod usermod
mkdir ~/public_html

```

then your site is accessible using
[http://localhost/~dvarsam/](http://localhost/~dvarsam/)

Then do your development on ~/public_html directory instead of /var/www[/QUOTE]


Dear "mlind",

Thanks for your reply!

I tried what you suggested, but it does not work:

root@ubuntu:/# sudo a2enmod usermod
This module does not exist!

Can you explain why it is not working for me & what exactly do the above commands you are suggesting do?
E.g.:

1. The command: "a2enmod usermod"...
    I visited "http://www.linuxdevcenter.com/linux/cmd/" & could not find a listing for 
    "a2enmod"...

2. Where exactly would I create the "public_html" directory?
    On my Desktop?
    And how would I tell "apache" to forward all visitors to my new "public_html" 
    directory, instead of the default "/var/www" one?

Thanks.

---

### Post by mlind on 2006-03-26
[QUOTE=dvarsam]Dear "mlind",

Thanks for your reply!

I tried what you suggested, but it does not work:

root@ubuntu:/# sudo a2enmod usermod
This module does not exist!

Can you explain why it is not working for me & what exactly do the above commands you are suggesting do?
E.g.:

1. The command: "a2enmod usermod"...
    I visited "http://www.linuxdevcenter.com/linux/cmd/" & could not find a listing for 
    "a2enmod"...

2. Where exactly would I create the "public_html" directory?
    On my Desktop?
    And how would I tell "apache" to forward all visitors to my new "public_html" 
    directory, instead of the default "/var/www" one?

Thanks.[/QUOTE]


Sorry, my fault. 

It's *sudo a2enmod userdir*.
~/  means your home directory. So if I execute *mkdir ~/public html*, it means
create directory /home/mlind/public_html. Don't do this as a root user!

You need to check out the documents about user directories if you don't
understand how Apache Httpd server maps directories. Usually user's directories
are mapped using protocol://server/~username/.

btw. you don't need to use sudo if you're already issuing commands as a root.

---

### Post by dvarsam on 2006-03-27
[QUOTE=mlind]

It is "sudo a2enmod userdir".

Then I can execute "mkdir /home/mlind/public_html"

Usually user's directories are mapped using protocol://server/~username/.

[/QUOTE]


Thanks for your Reply !!!


But of course, if I perform the following:

1. sudo a2enmod userdir

2. mkdir /home/mlind/public_html

_Question 1_:
Don't I have to tell the Ubuntu, that the "www" PUBLICLY ACCESSIBLE directory is NOT anymore in "/var/www", but instead in "/home/mlind/public_html"?

_Question 2_:
And how would I do this?

With the command:

DocumentRoot /home/mlind/public_html

And if "DocumentRoot" is the correct command to use:

_Question 3_:
Where would I add it?
Inside the Ubuntu file:

a. "httpd.conf"?
b. "apache2.conf"?
c. "ports.conf"?
d. or "/sites-available/default"?

Thanks for all your help!

---

### Post by mlind on 2006-03-27
[QUOTE=dvarsam]Thanks for your Reply !!!


But of course, if I perform the following:

1. sudo a2enmod userdir

2. mkdir /home/mlind/public_html

_Question 1_:
Don't I have to tell the Ubuntu, that the "www" PUBLICLY ACCESSIBLE directory is NOT anymore in "/var/www", but instead in "/home/mlind/public_html"?

_Question 2_:
And how would I do this?

With the command:

DocumentRoot /home/mlind/public_html

And if "DocumentRoot" is the correct command to use:

_Question 3_:
Where would I add it?
Inside the Ubuntu file:

a. "httpd.conf"?
b. "apache2.conf"?
c. "ports.conf"?
d. or "/sites-available/default"?

Thanks for all your help![/QUOTE]


1. No. Apache sees directories relatively. /var/www is the root directory of your web server,
user directory is below root directory. You shouldn't need to configure anything for userdir module,
except if you wan't to specify additional security constraints.

2. I'm not sure what you're after, but for configuring user directories once those are enabled, see
*/etc/apache2/mods-enabled/userdir.conf*

---

