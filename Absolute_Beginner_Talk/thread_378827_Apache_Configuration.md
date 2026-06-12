---
title: "Apache Configuration?"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by xunshirine on 2007-03-07
Hello. I intend to install mediawiki. Referring to [this pag]("http://meta.wikimedia.org/wiki/Help:Running_MediaWiki_on_Ubuntu_GNU/Linux")e, I can not configure apache appropriately. The copied steps are below.
>  sudo ln -s /etc/mediawiki1.7/apache.conf /etc/apache2/sites-available/mediawiki.conf
 sudo ln -s /etc/apache2/sites-available/mediawiki.conf /etc/apache2/sites-enabled/001-mediawiki
 
 sudo invoke-rc.d apache2 restart

The first step is ok. On second step there isnt any 001-mediawiki file on /etc/apache2/sites-available directory. Therefore apache restart fails. The terminal output ;
> ~$ sudo invoke-rc.d apache2 restart
 * Forcing reload of apache 2.0 web server...                                   grep: /etc/apache2/sites-enabled/001-mediawiki: No such file or directory
                                                                         [fail]
invoke-rc.d: initscript apache2, action "restart" failed.

And also in www directory there isnt any mediawiki directory, will I put it manually there?
Thanks in advance.

---

### Post by houstonbofh on 2007-03-07
The Apache stuff in Ubuntu was moved.  Asking why will start a religious war, so just let it go... :)  Just accept that going to [http://wiki.apache.org/httpd/Info/DistrosDefaultLayout](http://wiki.apache.org/httpd/Info/DistrosDefaultLayout) will answer your problems.

---

### Post by mahalie on 2007-05-28
Thanks for the info. Another newb here having the same problem. For others who stumble upon this, I removed the above created links:

```
sudo unlink /etc/apache2/sites-available/mediawiki.conf
sudo unlink /etc/apache2/sites-enabled/001-mediawiki
```

Per [a similar thread]("http://ubuntuforums.org/showthread.php?t=410201&highlight=001-mediawiki") to this I tried looking in /etc/ to see what the link should be and changed the links as such:

```
sudo ln -s /etc/mediawiki1.7/apache.conf /etc/apache2/sites-available/mediawiki.conf
sudo ln -s /etc/apache2/sites-available/mediawiki.conf /etc/apache2/sites-enabled/001-mediawiki 
```

The restart seemed to work but then I got a warning saying:
> [warn] The alias directive in /etc/apache2/sites-available/mediawiki.conf  at line #1 will probably never match because it overlaps an earlier alias.


However, going to [http://servername/mediawiki](http://servername/mediawiki) does get me a setup page so I proceed with the [installation instructions]("http://www.mediawiki.org/wiki/Manual:Running_MediaWiki_on_Ubuntu_GNU/Linux"). 

Other than changing "mediawiki" to "mediawiki1.7" following the instructions resulted in one working wiki!

:p

p.s. Oh crap, just noticed the new and improved installation instructions use these!!
[http://www.mediawiki.org/wiki/Manual:Running_MediaWiki_on_Ubuntu]("http://www.mediawiki.org/wiki/Manual:Running_MediaWiki_on_Ubuntu")

---

