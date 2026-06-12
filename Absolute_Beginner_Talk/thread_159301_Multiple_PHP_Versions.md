---
title: "Multiple PHP Versions"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by czambran on 2006-04-12
Does anybody knows how I can install multiple versions of php? I want to install php4 and php5.

Thanks

Christian

---

### Post by mandrakethepenguin on 2006-04-12
What purposes do you intend to use PHP 4 & 5 for (eg: Server Scripting)

---

### Post by czambran on 2006-04-12
yes, server scripting. 

I think I found a way to do it but apache needs to be compiled with the action module, does anobody know how to do this?

---

### Post by jameso on 2006-04-17
Hi,

Did you work out how to get php4 and php5 working on the same server?

I want to use php4 for all my .php files, and php5 for .php5 files. 

Thanks

---

### Post by czambran on 2006-04-17
I kind of gave up, I installed php5 as an apache module and php4 as CGI, but when I tried to run scripts using php4 it gave a weird error which I couldn't resolve. If you find a way to do it, I will really appreciate it if you could let me know.

Thanks 
Christian

---

### Post by Lezzles on 2007-05-08
So, is it possible to run php4 side by side with php5? I'd really appreciate some simple instructions.

I'm running Dapper and have php version 5 installed, but also need to run php 4 for an app that does not support version 5.

A **[comment by (lukasz at szostak dot biz) in the php manual]("http://es2.php.net/install.windows")** describes how he did it on Windows, which seems easy enough. Would the same work for Ubuntu?

I've only been using Ubuntu for a week, and am a little nervous of "just trying it" to see what happens. I really don't want to break php5 by installing php4.

---

### Post by LaRoza on 2007-05-08
You can do it at once as far as I know, but you can have both and switch between them.

---

### Post by Lezzles on 2007-05-08
Thanks for the super-fast reply LaRoza. I wonder if you could give more details. Did I say I was a total noob?

I want to have both versions running at the same time (not switch between them). In other words I want to be able to configure mysite.com/site1 to use php5 and mysite.com/site2 to use php4.

Is it [FONT="Courier New"]apt-get install php4[/FONT] to install version 4?

And then what do I do?

---

### Post by mech7 on 2007-05-08
How about XAMPP

[http://www.apachefriends.org/en/xampp-linux.html#611](http://www.apachefriends.org/en/xampp-linux.html#611)

> Because such very new versions like PHP 5 always should be handled with care we decided to include both current versions of PHP into XAMPP since version 1.4.7: PHP 5.x and PHP 4.x. If you find out your PHP application doesn't work with PHP 5 you will be able to switch back easily to PHP 4.

By the following command you can switch "back" to PHP 4.x:

/opt/lampp/lampp php4

And with the following command you can switch back to PHP 5.x:

/opt/lampp/lampp php5

If you forgot which version of PHP is in use simply use phpinfo() or call this command:

/opt/lampp/lampp phpstatus

btw You can't run two versions at the same that at least not that i know of.

---

### Post by LaRoza on 2007-05-08
XAPP is good, I use it on my flash drive and on my computers.

You can have both php version, but you can not use them at the same time, XAMPP makes it easy to switch back and forth.

---

### Post by Lezzles on 2007-05-08
Thanks guys. I will give XAMPP a go. It will suit the needs of my test environment just fine.

I will remember for future reference that php4 and php5 cannot be running at the same time. Out of interest, does the same apply to sub-versions? (ie. I assume you can't run 5.2 with 5.1?)

---

### Post by LaRoza on 2007-05-08
Why do you want to run more than one version at once?

I suggest you keep the most up-to-date version and the older version for testing purposes.

---

### Post by az on 2007-05-08
In Ubuntu, you can have both php4 and php5 installed on the same machine.  One instance of apache can only use one version of php at a time, though.

Whichever version of php you are running is determined by the apache module.  If you have libapache2-mod-php5, you are running php5.  Libapache2-mod-php4 will use php4.

Php4 is no longer supported in Ubuntu.  You can still get it in Dapper, but even the version in Dapper is unmaintained; basically, the same package as was in Hoary.

---

### Post by jameso on 2007-05-08
For the record, you CAN run php4 and php5 on apache at the same time.

You can only one run as an apache module, though. This means you must run the other as cgi.

I followed the (brief) instructions here: [http://wjd.nu/notes/2006](http://wjd.nu/notes/2006).

The instructions are for debian, but they also work for ubuntu.

In your case, you already have php5 running as an apache  module, so you would do the reverse to what they suggest there (ie replacing the word  php5 in their instructions with php4), installing php4 as a cgi module.

---

### Post by Lezzles on 2007-05-09
James, thank you!

I've followed as much as I can in those instructions, but am kinda stumped by
> Remember that this will only work when you actually do have /cgi-bin/ ScriptAlias'ed to /usr/lib/cgi-bin/  for the particular VirtualHost you want to use php5 on.

Can you give an example of this? Which file do I edit? I would want the default to be php5, and specify php4 for this one app (e.g. /var/www/site2)

---

### Post by jameso on 2007-05-09
Hi Lezzles,

On my server, I have php4 (apache module) as default.

For the sites that I want to run as php5, I have the following in the  /etc/apache2/sites-available/sitename file (at the bottom of the file (but before the existing </VirtualHost> line)):
```

ScriptAlias /php5-cgi /usr/lib/cgi-bin/php5

Action application/x-httpd-php5 /php5-cgi
AddHandler application/x-httpd-php5 .php .php5 .php4 .php3 .phtml

```

I would imagine that for the site2 site, you could add something similar to the code above, but replacing php5 with php4.

Site2 would have to be running as its own site in apache.

---

