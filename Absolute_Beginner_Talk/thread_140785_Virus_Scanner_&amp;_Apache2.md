---
title: "Virus Scanner &amp; Apache2"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by zwarrior on 2006-03-06
Hey all I just installed Aegis-virus-scanner and Apache2. I need help setting up these 2 programs.

1. How do I start Aegis-virus-scanner, update definitions, run scans, etc..
2. Apache is running, but how do I add a webpage, etc. Is there a GUI interface for this??

Thanks guys....

---

### Post by sas on 2006-03-07
To add a web page to apache you need to add files to the (as far as I remember)  /var/www-data directory, if it's not that exact one it's something in the /var/ directory.

---

### Post by zwarrior on 2006-03-07
do u know if there's any walkthroughs for any of these programs?

---

### Post by sas on 2006-03-07
[QUOTE=zwarrior]do u know if there's any walkthroughs for any of these programs?[/QUOTE]

For apache 2 there's probably quite a few, depending on what you want to do with it.
You could just google around but I couldn't tell you which ones are good tutorials and which ones aren't so good, mainly as I'm not sure what you're wanting to find out.

If you have any particular questions then ask here, in #ubuntu on irc.freenode.net or open a ticket on [https://launchpad.net/distros/ubuntu/+addticket](https://launchpad.net/distros/ubuntu/+addticket)

---

### Post by zwarrior on 2006-03-08
I just want to build a webpage, that's it. Running Apache in Windows is easy, but for Ubuntu/Linux/etc. is it all through command line? Isn't there GUI for this?

---

### Post by sas on 2006-03-08
[QUOTE=zwarrior]I just want to build a webpage, that's it. Running Apache in Windows is easy, but for Ubuntu/Linux/etc. is it all through command line? Isn't there GUI for this?[/QUOTE]

Sorry I told you wrong the directory is /var/www rather than /var/www-data
To get apache to start at boot you should use 'System -> Administration -> Services' and ensure the checkbox for apache is ticked.

To build a webpage create a html file as normal and put it in /var/www, this directory is owned by root, so you'll either have to use sudo to copy the files there or run 'sudo chmod 775 /var/www' and you can then use the directory like any other - using the filemanager to work in the directory.

You can then access the page by visiting [http://127.0.0.1](http://127.0.0.1)

If you're wanting to configure apache then it's either in /etc/apache2/ or /etc/apache/ depending on which version you're using.

If you're wanting a gui for editing the configuration file then I do not know of one, however it's pretty well documented in various places, and there's tutorials on the net for particular things you may want to do with it.

If you're trying to setup a LAMP server then [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP) may help.

---

### Post by az on 2006-03-08
[QUOTE=zwarrior]is it all through command line? Isn't there GUI for this?[/QUOTE]

A web server typically does not run an x server.  A web server typically only runs web server software.  No, there is no gui.  You don't need one.

---

### Post by dvarsam on 2006-03-08
Also read the articles on this (Ubuntu) Forum:

Article#: 87478
Article#: 115217
Article#: 132845

They should help you a little.

---

### Post by zwarrior on 2006-03-09
is there any "How-To" articles for setting this up for Noobs? I looked everywhere, but can't find good tutorial froms installing Apache2-->setting up webpages, etc. Any help? Thanks..

---

