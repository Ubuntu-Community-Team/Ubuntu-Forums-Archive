---
title: "Which options does apt-get use when compiling a package?"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by rossio on 2006-10-02
To the best of my knowledge, apt-get downloads and installs a designated package from an online repository. I suppose this could either be in the form of a pre-compiled binary, or as source which would then be natively compiled (transparent to the user, apt-get doing all the dirty work). Basically, getting rid of all the messiness of ./configure, make, make install. And of course, no dependency foolishness.

But what if I wanted to compile something from source that is offered from apt-get, with just a slight tweak to the options? Is there any way to easily tell which options apt-get would use by default?

As a concrete example, consider the package 'php5' which installs PHP version 5 (duh ;)). I want to re-compile PHP5 from source, because the default PHP5 package doesn't come with an extension I want to use. So I could download the source using *sudo apt-get source php5*, then *./configure --with-someextension*, etc., which is an option that the usual PHP5 installation of course doesn't use. But how can I tell what other options (*--enable-module=so, --with-xsl*, etc.) the "usual" apt-get install would have used? And can this be generalized to packages other than php5?

---

### Post by Jussi Kukkonen on 2006-10-02
*apt-get install* is binary-only.

If you want to tweak the compile settings, get the source like you did, but do not run configure: Instead edit debian/rules, and add your configure flags  there. The parameter to add your changes to is probably CONFIGURE_FLAGS, or something similar. Then run (in the source dir)
```
dpkg-buildpackage -rfakeroot -us -uc

```
Wait for dpkg to compile. The package should appear in the directory above  the source directory.

---

### Post by az on 2006-10-02
No.  Apt-get can do source packages as well.

sudo apt-get source php5

You need to have the source repos (deb-src) available.  Once the source package is downloaded and unpacked, you need to tweak the debian/rules makefile.


Are you sure that the php module you need is not already available as a seperate package?  Most of the time, these things are broken up into seperate packages.

---

### Post by rossio on 2006-10-02
(Before I say anything else, let me apologize for the length. At least I was thorough. If I did happen to leave anything out that you think might help you give an answer, or ask a more informed question, I'm happy to provide what I can!)


> **azz said:**
> Are you sure that the php module you need is not already available as a seperate package?  Most of the time, these things are broken up into seperate packages.


Quite sure, yes. I've already asked a related question [over here]("http://www.ubuntuforums.org/showthread.php?t=188629") in fact. The package I'm interested in installing is php5-imagick, however Dapper only has php4-imagick available. In trying to (re-)install PHP5 from source however I realized that this might be a more general problem (adding different compilation options to a standard package), which is why I started this second thread.

So I'm fairly certain I understood both your responses, which essentially advised the same thing (correct me if I'm wrong in thinking that). So here's what I did:

```
~$ mkdir php5-src
$ cd php5-src/
$ sudo apt-get source php5
```

Now on the recommendation of [the INSTALL file included with the imagick source files]("http://viewcvs.php.net/viewvc.cgi/pecl/imagick/INSTALL?revision=1.7&view=markup"), I move the untarred imagick files into a new directory under ext/

```
$ sudo mv ~/imagick ~/php5-src/php5-5.1.2/ext/imagick
```

Now comes the editing of the debian/rules file

```
$ sudo vi debian/rules
```

I search for "CONFIG", which leads me to a bunch of lines that start off with:

```
COMMON_CONFIG=  --build=$(PHP5_BUILD_GNU_TYPE)-gnu --host=$(PHP5_HOST_GNU_TYPE)-gnu \
                --mandir=/usr/share/man \
                --enable-memory-limit \
                --disable-debug \
                --with-regex=php \
                --disable-rpath \
                --disable-static \
                --with-pic \
                --with-layout=GNU \
                --with-pear=/usr/share/php \
... <many more lines> ...
                --enable-soap \
                --with-mime-magic=$(MAGIC_MIME) \
                --with-exec-dir=/usr/lib/php5/libexec
```


This looks promising, so I change that last line into two lines:

```
                --with-exec-dir=/usr/lib/php5/libexec \
                --with-imagick
```

I now ensure I'm in the right dir, then run debian/rules, followed by dpkg-buildpackage:

```
$ cd ~/php5-src/php5-5.1.2
$ sudo debian/rules
$ dpkg-buildpackage -rfakeroot -us -uc
```

Which then greets me, in part, with:

```
dpkg-checkbuilddeps: Unmet build dependencies: apache2-prefork-dev (>= 2.0.53-3) bison chrpath flex (>= 2.5.4) freetds-dev libcurl3-openssl-dev | libcurl3-dev libdb4.3-dev libgcrypt11-dev libgd2-xpm-dev (>= 2.0.28-3) libgdbm-dev libkrb5-dev libldap2-dev libmhash-dev (>= 0.8.8) libmysqlclient15-dev | libmysqlclient12-dev libpam0g-dev libpcre3-dev (>= 4.3-1) libpq-dev | postgresql-dev librecode-dev libsnmp9-dev | libsnmp-dev libsqlite0-dev libt1-dev libwrap0-dev libxmltok1-dev libxslt1-dev (>= 1.0.18) re2c unixodbc-dev
```

I assume I need all these *-dev packages because I'm using dpkg, not because php5 needs them (otherwise, these would have already been installed when I originally did *sudo apt-get install php5*, yeah?) so I dutifully type in *sudo aptitude install ...* followed by all of the above packages. Where there was a choice between two, I tried to choose the one that appeared to be more "general". I used aptitude, in case I make a mess and need to do some serious cleaning up.

Then I try once again:

```
$ dpkg-buildpackage -rfakeroot -us -uc
```

Which gives me writing errors, permission denied, etc., so I give up and just go with:

```
$ sudo dpkg-buildpackage -us -uc
```

This seems to go through, and ends up spitting out:

```
.....
dpkg-source: building php5 using existing php5_5.1.2.orig.tar.gz
dpkg-source: building php5 in php5_5.1.2-1ubuntu3.2.diff.gz
dpkg-source: cannot represent change to ext/imagick/examples/animated.gif: binary file contents changed
dpkg-source: cannot represent change to ext/imagick/examples/image.jpg: binary file contents changed
dpkg-source: warning: ignoring deletion of file ext/pdo/pdo_sql_parser.c.orig
dpkg-source: warning: ignoring deletion of file ext/date/lib/parse_date.c.orig
dpkg-source: warning: ignoring deletion of file ext/standard/url_scanner_ex.c.orig
dpkg-source: warning: ignoring deletion of file ext/standard/var_unserializer.c.orig
dpkg-source: warning: ignoring deletion of file ltmain.sh
dpkg-source: warning: ignoring deletion of file config.guess
dpkg-source: warning: ignoring deletion of file config.sub
dpkg-source: building php5 in php5_5.1.2-1ubuntu3.2.dsc
dpkg-source: unrepresentable changes to source
```

So now, where is my install (.deb?) file? Did dpkg-buildpackage do what it needed to do? I checked the directory above the source directory, and found the same files that were put there originally by the apt-get source download:

```
drwxr-xr-x 15 1003    4096 2006-10-02 11:54 php5-5.1.2
-rw-r--r--  1 root  969122 2006-10-02 11:55 php5_5.1.2-1ubuntu3.2.diff.gz
-rw-r--r--  1 root    1529 2006-10-02 11:55 php5_5.1.2-1ubuntu3.2.dsc
-rw-r--r--  1 root 8064193 2006-01-18 02:15 php5_5.1.2.orig.tar.gz
```

Not being very familiar with dpkg, I tried:

```
$ sudo dpkg -i php5_5.1.2-1ubuntu3.2.dsc
dpkg-deb: `php5_5.1.2-1ubuntu3.2.dsc' is not a debian format archive
dpkg: error processing php5_5.1.2-1ubuntu3.2.dsc (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 php5_5.1.2-1ubuntu3.2.dsc
```

So, I think I might be getting close.. but I'm not sure. Any more help would be greatly appreciated! And thanks already to those who have helped me so far. :D

---

### Post by Jussi Kukkonen on 2006-10-03
No problem. Nice to help someone who is ready to do the work and find things out for himself...

Your assumption that we advised the same thing is correct. I spotted two mistakes there though:
**1.** I should have mentioned this, but forgot: Use 
```
sudo apt-get build-dep php5
```
to install build dependencies. Apt is mostly overcautious about these, so the  packages might only be needed in some weird configs, but this is the easiest way to handle dependencies by far.

**2.** You used *sudo* with the *apt-get source* and *mv* commands. That's not actually needed and may screw things up as you then later run dpkg-buildpackage as the normal user (and the files it tries to modify are owned by root). I suggest starting fresh, if it's not too much trouble -- and avoid using sudo except when installing stuff (*apt-get build-dep* or *dpkg -i*). There's no need to run debian/rules by hand by the way, dpkg-buildpackage does that.

Then again, you seem to have fixed (or worked around) these two by yourself, so restarting might not be necessary... 

The build-process still doesn't succeed -- there should be a .deb as you thought... There seems to be a problem with imagick files, I imagine there was some more informative error message while it was building.

Some questions:
* Did you run phpize in imagemagick directory as suggested in INSTALL? (no idea what it does, just asking)
* Your debian/rules changes seemed fine, but The INSTALL also says: *If Imagemagick is installed in a non standard dir, add this dir to --with-imagick=dir*. This is very probable on Debian-based systems, you should try setting it (not sure what it should be though, /usr/bin maybe)

---

