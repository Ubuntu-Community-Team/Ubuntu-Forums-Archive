---
title: "ubuntu server: testing php and other things"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by pdoukas on 2007-09-16
I'm trying to install an application and run it on my server but I'm having a few issues so I want to troubleshoot what I feel are the necessary modules that need to be running.

The application is unimportant, nothing most of you would use, but it requires php, mysql, and apache. For that reason I installed the LAMP version of ubuntu server. The application itself installed quite easily but isn't running at all like it should......or possibly not at all.

I should be able to pull up something from a browser at [http://ipaddress/pacsone/home.php](http://ipaddress/pacsone/home.php) but I cannot. I can however pull up the apache directory at [http://ipaddress](http://ipaddress) and the only thing I see is a directory for apache. I was also under the impression that that I'd be able to see something if I went to the following address [http://ipaddress/pacsone/hello.php](http://ipaddress/pacsone/hello.php).

So I guess i need to know a few things:

1) Should there be a directory for pacsone (more info here [http://pacsone.com](http://pacsone.com))
2) How do I tell what versions of mysql, php, and apache that I am running.
3) How do I test php? Shouldn't I get something out of the hello.php 

Let me start there and I should be able to figure out a few things.

Thanks,

Pete

---

### Post by jamvegan on 2007-09-17
1) To access it with the sort of path that you're indicating, yes, there should be a directory named "pacsone" in /var/www/ (or whatever your document root is, if it's different).

2 & 3) Create a file containing the following:
[PHP]<?php
phpinfo();
?>[/PHP]
Call it something like php_info.php and place it in the document root.  With your browser, go to localhost/php_info.php (or ipaddress/php_info.php if you're accessing it from another machine).  If Apache and PHP are working, you'll see a webpage full of all the information you could possibly want.

2, if that doesn't work) Looking the packages up in Synaptic (System->Administration->Synaptic Package Manager) would probably be the easiest way to find the versions.

---

