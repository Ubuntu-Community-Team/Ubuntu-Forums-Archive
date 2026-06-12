---
title: "Apache default"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Nxion on 2007-06-27
Hi,

I have installed my apache and when i put the link in to test it. it goes to a page that says "Index of /" and i have to click on the "apache-default" link to get to my website. 

I need help !!!!!!!!!!

Thanks

---

### Post by scxtt on 2007-06-27
the root of your web server should be /var/www - or however it's config'd in apache2.conf ...

---

### Post by Nxion on 2007-06-27
It is

here is my link 

[http://beau.lunanet.biz/apache2-default/](http://beau.lunanet.biz/apache2-default/)

I want to be able to type [http://beau.lunanet.biz/](http://beau.lunanet.biz/) in a URL and it go there and NOT have the "apache2-default" part in there

How to I get rid of that ?

Thats what I am asking

Thanks

---

### Post by scxtt on 2007-06-27
so you're not doing anything to make it automatically forward [http://beau.lunanet.biz/](http://beau.lunanet.biz/) to [http://beau.lunanet.biz/apache2-default/?](http://beau.lunanet.biz/apache2-default/?)

what's the output of:

**ls -l /var/www**

and

**cat /etc/apache2/apache2.conf | grep -i documentroot**

also check out [https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html), which says:
> The DocumentRoot directive specifies where Apache should look for the files that make up the site. The default value is /var/www. No site is configured there, but if you uncomment the RedirectMatch directive in /etc/apache2/apache2.conf requests will be redirected to /var/www/apache2-default where the default Apache2 site awaits. Change this value in your site's virtual host file, and remember to create that directory if necessary!

---

### Post by Nxion on 2007-06-27
here is the out put of "ls -l /var/www*"

drwxr-xr-x 2 root root  4096 2007-06-26 13:06 apache2-default
drwxr-xr-x 2 root root  4096 1999-03-25 15:06 hostsentry-0.02
-rw-r--r-- 1 root root 33983 2004-08-06 21:33 hostsentry-0.02.tar.gz


[B]cat /etc/apache2/apache2.conf | grep -i serverroot*


# with "/", the value of ServerRoot is prepended -- so "/var/log/apache2/foo.log"
# with ServerRoot set to "" will be interpreted by the
# ServerRoot: The top of the directory tree under which the server's
ServerRoot "/etc/apache2"

[/B]

---

### Post by scxtt on 2007-06-27
how  about: **cat /etc/apache2/apache2.conf | grep -i documentroot**
(and you don't need to tack on a * to the end)

additionally, what's the output of **ls -l /etc/apache2**?

---

### Post by Nxion on 2007-06-27
[LEFT]Here is the output of   " ls -l /etc/apache2"

-rw-r--r-- 1 root root 24175 2007-01-15 11:10 apache2.conf
drwxr-xr-x 2 root root  4096 2007-06-26 13:06 conf.d
-rw-r--r-- 1 root root   895 2007-01-15 11:11 envvars
-rw-r--r-- 1 root root     0 2007-06-26 13:06 httpd.conf
drwxr-xr-x 2 root root  4096 2007-06-26 13:12 mods-available
drwxr-xr-x 2 root root  4096 2007-06-26 13:14 mods-enabled
-rw-r--r-- 1 root root    21 2007-06-26 13:13 ports.conf
drwxr-xr-x 2 root root  4096 2007-06-26 13:06 sites-available
drwxr-xr-x 2 root root  4096 2007-06-26 13:06 sites-enabled


Here is the output of "[B]cat /etc/apache2/apache2.conf | grep -i documentroot"

nothing comes up
[/B][/LEFT]

---

### Post by scxtt on 2007-06-28
try adding:

DocumentRoot /var/www/

to apache2.conf and restarting apache (**sudo /etc/init.d/apache2 restart**) and check again ...

---

### Post by Nxion on 2007-06-28
* Forcing reload of web server (apache2)...                                    Syntax error on line 51 of /etc/apache2/apache2.conf:
DocumentRoot must be a directory

fail

---

### Post by Nxion on 2007-06-28
I fixed it I didnt add the "" to it. But i reloaded apache2 and it STILL has the /apache2-default at the end of my website [http://beau.lunanet.biz](http://beau.lunanet.biz)

---

### Post by kspn on 2007-06-28
The issue is that in your /var/www Directory, you don't have an index.html file

That is the core of the website.

If you create an **index.html** file then it would be shown as the default page on your website.

EG
index.html
```
<html><head><title>Test Page</title></head>
<body>
<h1>This page is under Construction</h1>
</body>
</html>

```

Or you could just copy the contents of the **apache2-default** Directory into the **www** Directory then you don't need any redirection or anything like that.

*Edit: this was the original issue but as your web server is now doing an automatic redirect it may not work until you turn that function off (However it got turned on)*

---

### Post by Nxion on 2007-06-28
Im sorry but this is just leading me in circles. Thank you for trying to help me out.

---

### Post by kspn on 2007-06-28
The struccture of the default apache install is

/var/www
----/apache2-default
--------/index.html
--------//some other files

What it needed to be to fix the issue as originally demonstrated
/var/www
----**index.html**
----/apache2-default
--------/index.html
--------//some other files

---

### Post by Xeor on 2007-08-05
sudo gedit /etc/apache2/sites-available

change this:

	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                [COLOR="Blue"]**RedirectMatch ^/$ /apache2-default/**[/COLOR]
	</Directory>

to...

	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                [COLOR="Red"]**#**[/COLOR][COLOR="Blue"]**RedirectMatch ^/$ /apache2-default/**[/COLOR]
	</Directory>


That should do...

---

### Post by mogie on 2008-02-14
> **Xeor said:**
> sudo gedit /etc/apache2/sites-available

change this:

	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                [COLOR="Blue"]**RedirectMatch ^/$ /apache2-default/**[/COLOR]
	</Directory>

to...

	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                [COLOR="Red"]**#**[/COLOR][COLOR="Blue"]**RedirectMatch ^/$ /apache2-default/**[/COLOR]
	</Directory>


That should do...

It did ;) thanks

---

