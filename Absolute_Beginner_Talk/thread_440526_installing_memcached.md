---
title: "installing memcached"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by noaktree on 2007-05-11
I'm running Ubuntu Server 7 (latest) and have apache2 with php5 all running nice.

I've installed: apt-get install php5-memcache
I also have memcached installed: apt-get install memcached

Memcached is running, I checked with netstat -tap

I want to use memcached from php scripts. I entered $memcache = new Memcache; in a php script and of course I get an error about the Memcache object.

Next... pretend like I AM a complete noob and tell me step by step how to get php to communicate with memcached.

I found this blurb in the php memcached page:

/////////////

So, the steps:
	First - ./configure with --enable-memcache. This should show in your phpinfo() at the top (even though nothing of the memcache extension works yet).
	
	Second:
	either pecl install memcache
	OR
	download the source
	tar -xzvf [thesourcetarball]
	phpize
	./configure
	make
	make install
	
	Finally: Add extension=memcache.so to your php.ini. (If you don't have one, it should go in the root of where php is called ie., /usr/local/lib)

/////////////

MY QUESTIONS:

1) Memcached does not show up in my phpinfo(). I have no idea how or where to configure php to support memcached. How do I do this?

2) Is there a php.ini script by default install on Ubuntu Server? If so where is it located please.

3) Anything else I need to know?

Thanks,
Neil

---

### Post by noaktree on 2007-05-11
Fixed my own problem again! Man you guys are slow :) 

I just added dl("memcache.so"); to the top of my php script.

I'll just create a php.ini file and place extension=memcache.so in it. Once I restart my server all should be good. I hope. Anyways.. thanks for nothing. \\:D/

---

### Post by louis.landry on 2008-01-17
I realize this is an old post but I figured I would point something out.

The php5-memcache package installs everything correctly and adds a memcache.ini file to the path: /etc/php5/conf.d/

which is where all the individual php extension packages put their ini files to be read.  If you look at that file you will find that the line: extension=memcache.so is commented out with a semicolon preceding it.  If you uncomment that line then memcache becomes available and you can manipulate the other settings in the file as necessary.

- Louis

---

### Post by FlashUK on 2008-04-23
Hi,

Posting an update to this thread after I found it in google.

I am using Ubuntu 7.04 Feisty.

When installing php5-memcache it will automatically append the configuration to the /etc/php5/apache2/php.ini file.
It loads this extension like this:
"-e extension=memcache.so"
Remove the -e to get it working. Took me a while to figure it out but it works now. Hope this helps someone else.

---

