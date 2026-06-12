---
title: "index.php problem"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by RichJacot on 2007-03-30
Hello,  
I'm trying to install the gallery2 application and I've no more than just started and hit a wall.  I'm suppose point my browser (Firefox 2.0.0.3) to an index.php file in the install directory that was part of the extract.  I can browse to the install dir. just fine, but when I click on the index.php I get:

[IMG]http://www.flickr.com/photo_zoom.gne?id=439696908&size=l[/IMG]
[http://www.flickr.com/photo_zoom.gne?id=439696908&size=l]("http://www.flickr.com/photo_zoom.gne?id=439696908&size=l")

The question is, how do I open this in my browser to begin the install?

TIA!

---

### Post by ArieT on 2007-03-30
Gallery2 is het server-side application. Gallery2 is for websites etc. You must install apache if you really wants to use this application. What do you suspect gallery2 to be?

---

### Post by RichJacot on 2007-03-30
I realize that, but I'm just trying to get it installed.  I have apache2, mysql, imagemagik and php5 installed.  The instructions then state:

```
 Begin Installing  - Open up your web browser and browse to the install directory. Gallery 2 will walk you through the process of validating that your system is properly configured and will set everything up for you.
```

In the install directory is the index.php and my browser doesn't have an association to .php (I'm guessing).

---

### Post by raptor2552 on 2007-03-30
Do you have Apache, or a web server, installed on your computer? If not install it. I assume you have installed PHP, if not install it.

If you do have a web server installed, a php script must be in the web servers document root directory, /var/www by default in Apache. For example, move or copy gallery2 and all it's contents to /var/www so it looks like this: /var/www/gallery2. Now you'll be able to browse to [http://yourcomputer/gallery2/install/index.php](http://yourcomputer/gallery2/install/index.php) and have the php file execute.

---

### Post by indytim on 2007-03-30
If you've got LAMP properly installed and running, your protocol for launching pages within your web server are:

[http://localhost/](http://localhost/) <insert your directory/file path here>

ie
[http://localhost/gallery/index.php](http://localhost/gallery/index.php)

Hope this helps.

IndyTim

---

### Post by ArieT on 2007-03-30
But do you know how to use apache? You must move all gallery2 files into your webfolder. 

I guess you'd better learn how to use apache+php first: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by richbarna on 2007-03-30
> **RichJacot said:**
> Hello,  
I'm trying to install the gallery2 application and I've no more than just started and hit a wall.  I'm suppose point my browser (Firefox 2.0.0.3) to an index.php file in the install directory that was part of the extract.  I can browse to the install dir. just fine, but when I click on the index.php I get:

[IMG]http://www.flickr.com/photo_zoom.gne?id=439696908&size=l[/IMG]
[http://www.flickr.com/photo_zoom.gne?id=439696908&size=l](http://www.flickr.com/photo_zoom.gne?id=439696908&size=l)

The question is, how do I open this in my browser to begin the install?

TIA!

You have navigated to your temp folder on the computer, you need to access it from the outside (like when you surf the net). To do this (as long as you have apache running AND you have placed all your files in the /www folder) you just need to type > [http://localhost/install](http://localhost/install) in your browser and then you should be able to start the install and configure.

---

### Post by RichJacot on 2007-03-30
Ah... I see said the blind man.  

I now understand what I was doing wrong.  I'm down to the mysql php module and I thank you all very much!!!  This forum is GREAT!!!

Again Thank you!

---

