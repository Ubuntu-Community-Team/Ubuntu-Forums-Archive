---
title: "Executing RPM and DEB Files"
date: 2005-07-22
forum: Absolute Beginner Talk
---

### Post by OIDanTheManIO on 2005-07-22
I can't, for the life of me, figure out how to install programs that use .deb and .rpm files.  I'm REALLY new to Linux and I could really use the help.  Thanks.

-Dan The Man

---

### Post by DJ_Max on 2005-07-22
First, you don't use RPM's with Ubuntu, since Ubuntu isn't a redhat/RPM based distro.

To install a .deb package
```

sudo dpkg -i PACKAGEHERE.deb
```

---

### Post by varunus on 2005-07-22
The way you should get most of your programs is through Synaptic.  To use it, go to System->Administration->Synaptic.  It has a list of lots of software programs; get them through there if at all possible.

For the programs that you can't use synaptic for, its recommended to use a .deb file.  To install one, open a terminal, use "cd" to go to the directory the file is stored in, type "sudo dpkg -i packagename.deb", and enter your password.

RPMs can be installed too, but its not recommended unless you know what you're doing.  Most programs, even if you can't find them on the official program website, have a .deb package already in synaptic.  If you must install an rpm, use the command "alien packagename.rpm" in a terminal, followed by "dpkg -i packagename.deb" (alien converts rpms to debs).

One piece of advice; head over to [www.ubuntuguide.org](www.ubuntuguide.org) and follow the "Enable extra repositories" option.  It'll add a lot of potential installs to Synaptic.  The guide is useful in general for people new to Ubuntu.   :)

---

### Post by OIDanTheManIO on 2005-07-22
[QUOTE=DJ_Max]First, you don't use RPM's with Ubuntu, since Ubuntu isn't a redhat/RPM based distro.

To install a .deb package
```

sudo dpkg -i PACKAGEHERE.deb
```[/QUOTE]


This is what I got when I did that:

> root@oi:/home/dan # sudo dpkg -i /home/dan/Desktop/opera.deb
(Reading database ... 58113 files and directories currently installed.)
Preparing to replace opera-static 8.01-20050615.1 (using /home/dan/Desktop/opera.deb) ...
Unpacking replacement opera-static ...
Setting up opera-static (8.01-20050615.1) ...

-Dan The Man

---

### Post by DJ_Max on 2005-07-22
Ok, well there ya go. It should be installed.

I suggest you read a little.
[http://ubuntuguide.org](http://ubuntuguide.org)
[http://tldp.org](http://tldp.org)

There's a lot to learn.

Regards

---

### Post by varunus on 2005-07-22
Opera should either now be in your menus, or you should be able to start it from a terminal by typing "opera" or something similar.  You can use tab completion to help from a terminal;  type "ope" and then hit tab three times.  You'll see every command that starts with "ope."

Good luck.

---

