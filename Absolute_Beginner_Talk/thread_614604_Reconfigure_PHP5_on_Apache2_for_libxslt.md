---
title: "Reconfigure PHP5 on Apache2 for libxslt"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by carli on 2007-11-16
Hello everyone!

I have a problem understanding how to enable libxslt for use with PHP5 on Apache2.

I selected LAMP when installing Ubuntu Server ed. and I have added ionCube loaders succesfully by just adding a line in php.ini.

But when trying to enable libxslt, I wound up finding very little useful info on installing it. Both on [http://www.xmlsoft.org/](http://www.xmlsoft.org/) and other forums.

Heres what I've done:

1. Trying to just add it:
 1a. Configured and make'd libxslt on the machine.
 1b. Ran ldconfig -v and there it is.
 1c. Copied the libxslt to my php extensions dir.
 1d. Added the extension line in php.ini.
 1e. Restart Apache2. (sudo /etc/init.d/Apache2 restart)
 1f. Doesnt show up in phpInfo();.

2. Second shot. Recompiling PHP5
 2a. I read somewhere that PHP need to be built --with-xsl=/myxsltdir
 2b. Downloaded PHP5 source.
 2c. sudo ./configure --with-xsl=/usr/local/lib
 2d. sudo make 
 2e. sudo make install
 2f. Restart Apache2. (sudo /etc/init.d/Apache2 restart)

Still no luck.

I have also tried the 'sudo apt-get install libxslt-dev' which actually installs a package but I still dont get how to enable it in PHP5.

What have I missed as the n00bie I am on this platform?

---

### Post by carli on 2007-11-18
bump

---

