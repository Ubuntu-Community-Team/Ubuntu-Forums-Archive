---
title: "index.php not working in dapper"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by ggee on 2007-01-31
Not sure what I did wrong, but I can't get apache1/php4 to load index.php as a DirectoryIndex.  Everytime I go to the directory, it knows to load index.php, but it just wants to download it.  PHP files work fine if accessed directly.

<IfModule mod_dir.c>
    DirectoryIndex index.html index.htm index.shtml index.cgi index.php
</IfModule>

If I enter the following in the browser, it works fine.
[http://www/index.php](http://www/index.php)

but if I do the following, it wants to download some application/x-httpd-php.

[http://www](http://www)

Obviously, I missed something small.  Thanks for any tips.  I have had not problems with this kind of stuff for years, but I am new to Ubuntu and I might have missed something.

I am running Apache 1 and PHP4 in Dapper.

Thanks,
Greg

---

### Post by ironfistchamp on 2007-02-23
For a start would in not make sense to use apache2/php5? I'm pretty sure they are in the repos. 

Anyway I would have thought it was because you were not typing a full domain name. If you type localhost or 127.0.0.1 then it should bring it up. If you have a full domain name then type that in and it should work. 

I'm not very network savvy (I should be I'm doing the CCNA course) but that is what I would think.

HTH

Ironfistchamp

---

