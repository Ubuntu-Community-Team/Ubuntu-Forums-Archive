---
title: "Damn Small Linux, Monkey Web Server, &amp; PHP"
date: 2011-10-30
forum: Any Other OS
---

### Post by kevinharper on 2011-10-30
I installed DSL on a REALLY old computer. I want turn it into a web-server that runs internally, within my LAN.

DSL has Monkey Web Server built-in. I've configured it so that it starts when the computer boots up (I also set BetaFTP and SSH to start on boot).

I can add files to /opt/monkey-0.9.2/htdocs but I cannot get PHP files to display properly.

I installed the "php-4-monkey-0.9.1.tar.gz" package listed in the MyDSL Browser. After installing the package, I now have a php folder at /opt/ (this php folder wasn't there before the php package install).

If I create the following document:
```

<?php
phpinfo();
?>

```
and save it as /opt/monkey-0.9.2/htdocs/filename.php I see the source code instead of what the script should spit out.

It's been a while since I messed around with configurations and setting up web servers... What's my next step?

---

### Post by kevinharper on 2011-10-30
I have been very tempted to install XAMPP on top of DSL or even remaster LAMPPIX...

But I think I am so close. I know it's a simple thing that I have overlooked.

I haven't found a way to get Monkey Web Server to execute my PHP scripts. The server has perl and lau already installed but I would really, really like to use php. I only need basic query interactions w/ sqlite (db installed on DSL) to serve webpage content.

---

### Post by kevinharper on 2011-10-30
AHHHH! This is exactly what I am experiencing...
[http://www.damnsmalllinux.org/f/topic-3-7-9486-0.html](http://www.damnsmalllinux.org/f/topic-3-7-9486-0.html)

But I have restarted the web server... :( I have even restarted (repeatedly) the computer itself.

Still unable to execute php scripts.

---

### Post by kevinharper on 2011-10-30
BAHM!

So after restarting my pc a few times I decided to restart the web server...

I have no clue how this happened, but I was getting an error saying that the root directory wasn't correct. I was previously able to restart without a problem but, again, somehow something changed.

What changed? Not sure if dir-name or the entry in the config file. I know it sounds crazy but I didn't change anything and it all-of-the-sudden stopped working on it's own.

I made the following change on /opt/monkey-0.9.2/conf/monkey.conf:

Changed "Server_root /opt/monkey-0.9.1/htdocs" to "Server_root /opt/monkey-0.9.2/htdocs". Saved the file and restarted the web server.

EDIT: I uninstalled php, installed gcc1(with utils) and then reinstalled the php package specific for the Monkey Web Server... The path in the config file was reverted to "...-0.9.1...".

BAHM! Thanks guys!

---

