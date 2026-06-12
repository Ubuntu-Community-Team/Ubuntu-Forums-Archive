---
title: "Sipie problems"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by clancymf on 2007-10-03
I posted this on the Sirius forum but it is over 80+ posts (see [http://ubuntuforums.org/showthread.php?t=284893](http://ubuntuforums.org/showthread.php?t=284893))

I cannot seem to get the player working... Any ideas would be GREATLY APPRIECATED!!!  I miss Howard Stern 

--------------------------------------------------------------------------------

I did the following:
clancymf@clancypc:~$ sudo easy_install --upgrade sipie
Searching for sipie
Reading [http://cheeseshop.python.org/pypi/sipie/](http://cheeseshop.python.org/pypi/sipie/)
Couldn't find index page for 'sipie' (maybe misspelled?)
Scanning index of all packages (this may take a while)
Reading [http://cheeseshop.python.org/pypi/](http://cheeseshop.python.org/pypi/)
Reading [http://cheeseshop.python.org/pypi/Sipie/0.1179843539](http://cheeseshop.python.org/pypi/Sipie/0.1179843539)
Reading [http://eli.criffield.net/sipie/](http://eli.criffield.net/sipie/)
Best match: Sipie 0.1190648273
Downloading [http://downloads.sourceforge.net/sip...0648273.tar.gz](http://downloads.sourceforge.net/sip...0648273.tar.gz)
Processing Sipie-0.1190648273.tar.gz
Running Sipie-0.1190648273/setup.py -q bdist_egg --dist-dir /tmp/easy_install-jTQsJf/Sipie-0.1190648273/egg-dist-tmp-QJ0jQO
Adding Sipie 0.1190648273 to easy-install.pth file
Installing sipie.py script to /usr/bin
Installing cliSipie script to /usr/bin
Installing gtkSipie script to /usr/bin
Installing wxSipie script to /usr/bin

Installed /usr/lib/python2.5/site-packages/Sipie-0.1190648273-py2.5.egg
Processing dependencies for sipie
clancymf@clancypc:~$ gnome-terminal -x /usr/bin/sipie 
clancymf@clancypc:~$ 

It looks like it worked but when i run the gnome-terminal -x /usr/bin/sipie the screen just flashes and nothing...

---

### Post by ajgreeny on 2007-10-03
I have no idea whether the link you gives would eventually lead you to this but there is a google link to here [http://ubuntuforums.org/showpost.php?p=1789365&postcount=4](http://ubuntuforums.org/showpost.php?p=1789365&postcount=4) as #8 on a search of sipie.  See if it helps.

---

### Post by clancymf on 2007-10-03
Thanks for your help.  I have tried just about everything in the guide, including those commands.  It appears that the developer has just updated the tool so maybe others will have the same results as me and a solution can be developed.

---

### Post by clancymf on 2007-10-04
Solved :)
I needed to run sipie.py

---

