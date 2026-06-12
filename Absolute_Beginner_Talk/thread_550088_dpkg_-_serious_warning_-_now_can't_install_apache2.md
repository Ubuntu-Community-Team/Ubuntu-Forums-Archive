---
title: "dpkg - serious warning - now can't install apache2"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by pizzipie on 2007-09-13
My initial goal was to install apache2.   By mistake I did **sudo apt-get install apache.** I then tried to remove apache and install apache2. I could never get apache2 to run. I then tried to remove apache2 and start over. Every time I did **sudo apt-get apache2** I got a message saying that apache2 was installed. I then removed every file that had the word** apache* **in it trying to tell dpkg that apache or apache2 was not installed. I now get a **serious warning **about dpkg ( see attachement). Finally in total frustration I downloaded the source for** apache2 (v 2.2.3-3.2ubuntu0.1) **Since I had never installed any program from source files before I was amazed to see that apache2 worked. However, after trying to get PHP5 to work with apache2 I am now getting messages that apache2 can't find files for PHP5.  Apache2 was installed into /usr/local/apache2. I know that apt-get installs into /etc/apache2. I am usy Feisty-July 2007 and up-to-date.

The bottom line is: [B]How do I undo everything I have done, fix dpkg and then install apache2 properly with apt-get.

Thanks in advance for anyones help.

RP
[/B]

---

### Post by bwhitaker on 2007-09-13
There are several things that may help, before doing anything I would suggest backing up any important information, including config files you've modified.


Neither of these next should do anything to a working system:

This will often times either install or remove pacakges in inconsitant states:
```

sudo apt-get -f install

```

This should make it attempt to download and install missing packages
```

sudo apt-get --fix-missing

```


These may break things in a working system( pretty much just the packages itself not apt or dpkg)
Since it belives apache is installed you may want to try to remove it
This tells apt to remove the patache and any packages that depend on it
```

sudo apt-get remove apache2

```

This tells dpkg to completely remove anything that was installed with package, mainly config files, since these normally get left behind
I can't recall how many packages should be installed for apache2 but I would suggest purging all of them
```

sudo dpkg purge packagename

```

Then reinstall:
```

sudo apt-get install apache2

```

Or if you're going to continue using the source install, you probably need to go ahead and compile php from source as well and tell it where to find apxs2(the apache module tool).  Using the configure switch:
 -with-apxs2=/usr/local/apache2/bin/apxs

Hope this helps.

---

### Post by pizzipie on 2007-09-13
Thanks for early reply bwhitaker!

How do I remove Apache2 that I installed from source and is in the wrong PREFIX ( /usr/local/apache2). Does dpkg do this?

R

---

### Post by bwhitaker on 2007-09-13
dpkg is the debian package tool which allows you to install .debs.  Apt-get is actually a front end to dpkg.  So unless it was installed from a .deb it will not allow you to remove it.  However there really isn't such a thing as a wrong prefix, I normally install apache into /usr/local/apache or /usr/share/apache.  Since you used a prefix if you want to remove it all you should have to do is remove the directory as everything should be contained inside the prefix folder.

---

### Post by pizzipie on 2007-09-13
I did some further research and found an article in **[http://www.debian-administration.org/articles/](http://www.debian-administration.org/articles/)... entitled "Dealing with troublesome package upgrades or removals". **

In summary, it says in **/var/lib/dpkg/info/PACKAGENAME **there appear files as so:
**PACKAGENAME.postinst,  .preem, and  .postrm. **

These scripts begin** #!/bin/sh -e**. The recommended solution was remove the -e.  This worked for me as it allowed the **apache2-mpm-worker.prerm** to remove the file. It then installed ok with Synaptic Package Manager.

I am still puzzled however as the install did not put httpd.conf in /etc/apache2/conf/ where it the program is looking for it.

Any ideas. Is there a published Ubuntu Layout to install to?

Thanks again,
R
.

---

### Post by bwhitaker on 2007-09-13
when using a prefix all files are installed into the prefix directory.  There are a couple of ways around this. Some packages allow you to specify a config directory, with this it will install the configuration files into a normal location like /etc.  Apache2 doesnt seem to have an option like this.  You can however make a symbolic link for it.

of course fix the paths to match you're system
```

sudo ln -s /usr/local/apache2/conf /etc/apache2/conf

```

I normally also link the logs to /var/logs/apache when i'm buiding a web server(unless var and usr are on different partitions.

```

sudo ln -s /usr/local/apache2/logs /var/logs/apache

```


As to a typical location for ubuntu or debian, it's installed into normal program locations.  The logs into /var/log/ the config files in /etc/, binaries in /usr/bin/.  Typially, I've found it's best to do an entire service from source or from packages, it can be tricky trying to mix them.  By service I mean, compile both apache and php + php libs, or a mail sever like postfix or qmail and it's accessories.  Of course this is not a necessity, I've just found it to be easier.


Hope this helps

---

### Post by pizzipie on 2007-09-14
Thanks a lot,

I think I have a good feel for what is happening now. I've got apache2 running and PHP5 works with it now.

R

---

