---
title: "netatalk not working with default install"
date: 2008-08-24
forum: Apple Hardware Users
---

### Post by lone1 on 2008-08-24
hey guys,

I just "apt-get install netatalk"'ed on hardy, went to my mac (10.5.4), cmd-k afp://linux.host, typed my name and passwd and nothing worked. my mac said something like "server's not there, can't conncet" (error -5002). 

any explanations? shouldn't it be that easy?

---

### Post by Cheesehead on 2008-08-24
1) Did you get any errors when installing Netatalk? There are a few known, unresolved bugs.

2) Is the mac or other appletalk device on the network when you boot your linux box? If not, the appletalk daemon (atalkd) will turn itself off.
Check System Monitor or top to see if atalkd is running. 
To restart the appletalk daemon on Ubuntu use the command 'atalkd'. It has a man page with options, too.

3) Did you set up sharing on the linux box? Otherwise you'll be able to connect, but not access anything.

---

### Post by tiresia on 2008-08-24
You have two situations:
1. MacOS server - Ubuntu client 
Here you must just set it in System Preferences in MacOSX

2. Ubuntu Server - MacOS Client  
Here you should at least configure the file /etc/netatalk/AppleVolumes.default, in order to specify which Files or Folders you want to share, and the users and groups that can access this Files.
Therefore make sure that you have such a file
```
ls /etc/netatalk
```
```
sudo nano /etc/netatalk/AppleVolumes.default
```

There you must add
```
path [ volume name ] [ options ]
```

For more informations:
[http://netatalk.sourceforge.net/2.0/htmldocs/](http://netatalk.sourceforge.net/2.0/htmldocs/)
[http://netatalk.sourceforge.net/2.0/htmldocs/AppleVolumes.default.5.html](http://netatalk.sourceforge.net/2.0/htmldocs/AppleVolumes.default.5.html)

---

### Post by sayad on 2008-08-24
i agree with tiresia on the second situation.
the scripts arre important in that fact.

---

### Post by cyberdork33 on 2008-08-24
> **lone1 said:**
> hey guys,

I just "apt-get install netatalk"'ed on hardy, went to my mac (10.5.4), cmd-k afp://linux.host, typed my name and passwd and nothing worked. my mac said something like "server's not there, can't conncet" (error -5002). 

any explanations? shouldn't it be that easy?

Yea, you have to actually configure things and such before anything is shared... Just installing won't give you a working share.
[http://ubuntuforums.org/showthread.php?t=410274](http://ubuntuforums.org/showthread.php?t=410274)
[http://ubuntuforums.org/showthread.php?t=347019](http://ubuntuforums.org/showthread.php?t=347019)

---

### Post by lone1 on 2008-08-24
> **cyberdork33 said:**
> Yea, you have to actually configure things and such before anything is shared... Just installing won't give you a working share.
[http://ubuntuforums.org/showthread.php?t=410274](http://ubuntuforums.org/showthread.php?t=410274)
[http://ubuntuforums.org/showthread.php?t=347019](http://ubuntuforums.org/showthread.php?t=347019)

do you read the things you post? it's a guide about how to *re-compile* netatalk so it uses encrypted authentification

I do have somewhat experience with netatalk (way back). there is a default share in AppleVolumes.default, you don't have to configure anything. I just wonder what the package maintainer was thinking, it seems he didn't even run one simple test!

---

### Post by cyberdork33 on 2008-08-24
> **lone1 said:**
> do you read the things you post? it's a guide about how to *re-compile* netatalk so it uses encrypted authentification
yes i noticed that. I almost opted not to post that one, but it does have links to more information. I thought it might help you to look through. If not then ignore it. No reason to be rude. 

If you have a config setup already, then naturally, if you have a problem, posting it would be the best course of action to lead to a diagnosis.

---

