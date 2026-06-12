---
title: "Images Not Appearing in Apache2 on Localhost"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by jsweeney on 2007-09-02
I'm having a problem with web pages that I am creating on an Ubuntu 7.04 box with Apache2, Tomcat, MySQL, and PHP installed.

The problem is that I cannot get images to display on pages that I write. For example:

<html>
	<head>
		<title>Home Page</title>
	</head>
	<body>
		<img src='images/logo.gif'>
	</body>
</html>


When I load this page using [http://localhost/index.html](http://localhost/index.html), the image does not display, even though the folders and files exist. I've double-checked the casing on the names, I know that Linux is case sensitive.

When I open the URL [http://localhost:8180](http://localhost:8180) for the Tomcat home page, I see images just fine.

Now, before you respond, some background about me:

I've been designing websites in a Windows environment for 12 years. I have experience with IIS, Apache, Tomcat, ASP, .Net, JSP, PHP, SQL Server, Oracle, and MySQL - again, all in a Windows environment.

I'm new to the Linux environment, so I suspect the problem is in permissions or a config somewhere. I'm still having some trouble making sense of a lot of it. It's a brave new world for me!


Thanks!

---

### Post by ericmitz on 2007-09-02
try giving the full path to the image the src tag. like src=http://localhost/images/logo.gif 

that will tell you if you're having problems with your path..

---

### Post by dangerworm on 2007-09-07
I was also having this problem. I checked the error logs, file permissions, apache configuration files and the rest, and couldn't figure it out. Turned out I'd written 'ScriptAlias /images/ /<images path/' in /etc/apache2/sites-available/default and needed just a simple 'Alias' instead. HTH.

---

