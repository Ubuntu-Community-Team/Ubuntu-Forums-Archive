---
title: "curl and php5"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by syvehc on 2007-04-13
I used "apt-get install php5-curl" to install curl and now I was wondering how to confirm it is working.

Do I need to add a line to the php.ini to enable it?

My main goal it to make it work with a application called sugarcrm and a groupwise plugin.  The app seems to need a "--with-curl=" function in php.ini, however I am unsure about this and I figured there must be some standard setup of curl with ubuntu 6.10, php5 and a test that can be performed to see if it is working properly.

Thanks in advanced.
Tom

---

### Post by Stickymaddness on 2007-04-16
I'm not familiar with curl, but I'm guessing if it's installed properly and you ran

```

<?php
     phpinfo();
?>

```

It will show curl under extensions....

---

### Post by syvehc on 2007-04-16
Thanks, that did it, it did shows as enabled.  I did do one other thing though for those interested I ran "apt-get install curl"  I guess I thought the php5-curl was all I needed.  Now that I restarted apache the application doesn't have that error.  Now the last thing I need it to add a cron job which is new to me but I think I can handle it.

Thanks for the help.

Tom

---

### Post by Green Lantern 4 on 2008-03-09
Hi

You need to add line like this in you php.ini file

extension=gd.so
extension=mcrypt.so
extension=curl.so

It's a good idea to check that you have them installed on your system by looking in:

/usr/lib/php5/20060613+lfs (on my gutsy)

Regards

---

