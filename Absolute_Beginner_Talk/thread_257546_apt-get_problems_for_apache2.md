---
title: "apt-get problems for apache2"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by jmwhokie on 2006-09-14
I was trying to do an install of apache2, which did fine. But i hosed it, and wanted to just start from scratch. I did an apt-get remove, but had ALSO manually removed the directors (like in /etc/apache2...etc)
The apt-get install doesn't seem to want to put them back, and/or config init.d...etc
any ideas? It's driving me CRAZY

---

### Post by Jussi Kukkonen on 2006-09-14
I believe it's not putting them back because it 'knows' you've changed things by hand -- normally that means they shouldn't be touched...

The normal way of removing the app and all config files is
```
apt-get remove --purge apache2
```
Try that, and then reinstall

---

### Post by jmwhokie on 2006-09-14
well, i did try that (and did it again)
still no love.

i may just try and get the sources from sourceforge and compile..but i really don't want to do that. I like the ease of apt-get, but find it strange that it will install directories and config files , but not if they've been manually altered.
:confused:

---

### Post by jmwhokie on 2006-09-15
Any other thoughts folks?

Thanks in advance!

---

### Post by jmwhokie on 2006-09-15
So....i'm still digging around on this....ANYONE EXPERIENCED THIS YET?

Re-summary....

Did apt-get apache2...great. fine. happy

Did some stuff...and wanted to reinstall it.

I manually deleted the config files (oops...that is where my problems began)

and now an apt-get install (after a remove with purge) won't reinstall ANYTHING...
even though it "looks" like it was done if i do an unistall...

All I want at this point is a FRESH apache2 install...and i'm not really wanting to grab the sources from apache and build the thing just yet.

---

### Post by j2d3 on 2007-05-03
I wish I could offer a solution.  I am experiencing the very same problem right now and it is ultra annoying because I have a yesterday deadline for repairing this machine.  it was a redhat box acting as our mass mailer.  there were several probs and I wanted to change it to ubuntu.  i backed up my important stuff, wiped it, put ubuntu on it, and then started installing all the stuff i need with apt-get, which normally i love.  

i think i did the exact same thing as you.  i installed apache2, no trouble.  i hosed it by overwriting apache2.conf and this was just moments after installing, so i just removed the package thinking i'd reinstall and it would be back to how it was, but it won't recreate the /var/www or /etc/apache2 directories.  it just won't reinstall.  

if you figure it out please post it!

---

### Post by jfinkels on 2007-05-03
What output do you get when you try to install it using aptitude? Perhaps that would help the community to help you.

---

### Post by posborne on 2008-07-11
I am also experiencing the same problem... I may end up building apache from source in order to get things working (though this is less than desirable because I prefer things to be a part of the package management system).

I have had apache installed before, but somewhere along the line wanted to start over, so I removed apache2 (sudo apt-get remove apache2) and installed again using apt-get...

Here is output from a session, as you can see, none of apache's configuration files are present when I do an ls at the end.
```

osbpau@N3-314:/etc/apache2$ sudo apt-get remove --purge apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  apache2*
0 upgraded, 0 newly installed, 1 to remove and 190 not upgraded.
After this operation, 102kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 217879 files and directories currently installed.)
Removing apache2 ...
osbpau@N3-314:/etc/apache2$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 190 not upgraded.
Need to get 0B/44.6kB of archives.
After this operation, 102kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 217873 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.8-1ubuntu0.3_all.deb) ...
Setting up apache2 (2.2.8-1ubuntu0.3) ...
osbpau@N3-314:/etc/apache2$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]
osbpau@N3-314:/etc/apache2$ ls /etc/apache2/ /etc/apache2/conf.d/
/etc/apache2/:
apache2.conf  httpd.conf      mods-enabled     sites-enabled
conf.d        mods-available  sites-available

/etc/apache2/conf.d/:

```

---

