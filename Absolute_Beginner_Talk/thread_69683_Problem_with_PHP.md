---
title: "Problem with PHP"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by Slanter on 2005-09-27
Hi,
Im new to Linux and Ubuntu. I  have installed Ubuntu and apache, mysql and php. When I installed apache and php I apt-get and installed this packages:

```
apt-get install apache2 apache2-common apache2-doc apache2-mpm-prefork apache2-utils libapr0 libexpat1 ssl-cert 

apt-get install autoconf automake1.4 autotools-dev libapache2-mod-php4 libkrb53 php4 php4-common php4-dev php4-imagick php4-mcrypt php4-rrdtool php4-sqlite php4-curl php4-domxml php4-gd php4-imap php4-ldap php4-mcal php4-mhash php4-mysql php4-odbc php4-pear php4-xslt 

```

But when I try to load a php page I get "Do you want to open or save this file" dialog.

I guess I havent installed php properly but I dont know how to do it.

Can anyone help me please?

/Slanter

---

### Post by fmasi on 2005-10-05
I have exacly the same isue so if enny one could help us thx

---

### Post by Yako on 2005-11-02
You have to uncomment a few lines in Apache's httpd.conf. Something to do with mime types.

---

### Post by MakubeX on 2005-11-04
Really? Are you sure you are accessing the page via localhost?

---

### Post by trevdiggy on 2005-11-08
I'm working to fix the same problem on my system.  Here's what I've found so far:
Apache2 on Breezy does not require any un-commenting in httpd.conf - in fact, httpd.conf is a dummy placeholder file now.  
Instead, Apache2 on Breezy uses symlinks in the mods-enabled directory (default: /etc/apache2/mods-enabled) that point to .load and .conf files in the mods-available directory.

My default apache install using Synaptic had the appropriate symlinks to php5.conf and php5.load in the mods-enabled directory.  But still, Firefox asks me if I want to open or save each time I navigate to [http://127.0.0.1...BUT](http://127.0.0.1...BUT) -- it turns out if I explicitly go to a php file other than the index (e.g. - [http://127.0.0.1/myfile.php)](http://127.0.0.1/myfile.php)), Firefox renders the page as normal.  Also, Mozilla was able to open the index .php file at [http://127.0.0.1](http://127.0.0.1) just fine.  

Just thought I'd help us accumulate a little more ignorance here...

Anybody have a solution?

---

### Post by lreyes6 on 2005-11-08
Ok... the problem it's because there's something that have to be installed... 
let's say that you have an apache2 installed and the problem is only with the php... on my ubuntu breezy i have this packages installed (i use php4) 
[LIST=1]
[*]php4
[*]php4-cli
[*]php4-common
[*]libapache2-mod-php4
[*]php4-mycrypt
[*]php4-mysql
[*]php4-pear
[/LIST]

i think that if you want to install php5 the packages are alike

hope this help

---

### Post by SuperMike on 2005-11-25
[QUOTE=Yako]You have to uncomment a few lines in Apache's httpd.conf. Something to do with mime types.[/QUOTE]

No, not quite. The real story is that Ubuntu puts a hook in the apache2.conf so that it knows to look somewhere else for the Mime type arrangement. It's in /etc/apache2 or /etc/php4 or /etc/php5, I think I recall from my research last night. Try catting the text files in those directories and you'll finally find the Mime type arrangement in the uncomment form, while in apache2.conf it is commented out like it is supposed to. And the Ubuntu install does this for you if it's been setup right. The problem is that the Ubuntu Breezy install is intermittently flaky. When I finally got mine to work, my Mime type entry was *not* in apache2.conf but was in another file. And httpd.conf is old and obsolete, only there for backwards compatibility in some cases.

I think I'm seeing a pattern of an undocumented Ubuntu Breezy bug in PHP5 and PHP4 installs with the libapache2-mod-php4 or libapache2-mod-php5. If you uninstall and reinstall multiple times, you'll find that it just sort of works if you repeat the process several times. I had to repeat the same exact process like 5 times on my PC before it just worked. And when you uninstall PHP, it will warn you that libapache2-mod-php(x) didn't get installed in the first place, so it can't remove it.

My running theory here is that either there's a bug in the Canonical web farm with some of the mirror servers we're hitting. I cannot figure out any other reason why the libapache2-mod-php(x) would install one time and not another.

And if you do a search on ubuntuforums.org, you'll find that a lot of people are having this issue. The net effect of this is that even though you have installed Apache2, PHP(x), and libapache2-mod-php(x), and have cleared your Firefox cache, you find that Firefox still asks you what to do with the PHP file, instead of Apache2 pre-processing it at the server. This is because the libapache2-mod-php(x) is failing to be compiled and inserted properly into the Apache2 framework -- even though you can clearly see the various .conf files are properly updated and the libphp(x).so file is in the proper place.

I finally got my PHP4 to work in Breezy. A couple days ago, I also had my PHP5 working too. So it *can* be done. Just keep playing with Synaptic and the install, trying different ways to install it, or install just what you need first and add other extra PHP items you need as you go. You'll find if you keep fighting with it for like 4 hours, it finally just *works*, somehow.

I wish there was a way I could easily report this as a bug to be checked. If you all know where to post this, let me know. The bug can be easily reproduced. Just upgrade from Hoary (with a loaded PHP4 install) to Breezy, and then uninstall completely the PHP4 and/or PHP5. Then, reboot. Then, try to install PHP4 again with Universe option enabled. Or, for that matter, try on a separate PC to install PHP5 again. Both PHP4 and PHP5 will intermittently have the same issue of not compiling the libapache2-mod-php(x) file properly.

I'd also like to know how I can become a tester for Canonical's PHP installs. It sounds like they didn't test this very well and could stand to have a developer help them.

---

### Post by ExemplarUbuntu on 2005-12-05
Edit the apache2.conf file and find the line AddType ..... .php

Uncomment this line, save the file and apache2 -k restart

PHP will now process the .php files on your server and this stops
your browser trying to download the file.

---

