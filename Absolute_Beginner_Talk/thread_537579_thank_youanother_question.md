---
title: "thank you/another question"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by metsfan47 on 2007-08-29
Before my question, a big THANK YOU to everyone for helping me get Ubuntu up and running.  I am now Windows free!!  I had tried and failed for months without coming on here for help.  Everytime I've tried to get help on a tech forum, the results were usually something like "stupid n00b, im l33t" etc.  Everyone was so nice and helpful, thank you again!

I'm attempted to burn/play .mp3 files in my newly installed and working Ubuntu.  After researching the forums it seems I needed to install "gstreamer extra plugins".  However when I attempt to do this, I get the following error:

"Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)"

Anyone know what I'm doing wrong?  Thank you guys in advance!!

-Aaron

P.S.  My most often used keyboard shortcut in Windows was "Windows Key + D" to minimize everything and go to the desktop.  does anyone know if there is an Ubuntu equivalent?

---

### Post by hyper_ch on 2007-08-29
well, please use a descriptive title for your problem... that makes it easier for people to help...l

Might be that the us archive currently has a few issues.

Solution:

(1) Open the sources.list in an editor
```

gksudo gedit /etc/apt/sources.list

```

(2) replace the "us" with another country.
e.g.  ch is for switzrland,  de for Germany,  fr for France... you maybe want to use ca for Canada

(3) save the altered sources.list

(4) run the update:
```

sudo apt-get update

```

---

### Post by xtapolapaktl on 2007-08-29
Don't know about your initial question but I can answer this:

> 

P.S. My most often used keyboard shortcut in Windows was "Windows Key + D" to minimize everything and go to the desktop. does anyone know if there is an Ubuntu equivalent?
I believe the default is CTRL-ALT-D, but you can change this in the Keyboard Shortcuts menu in System->Preferences.

The option is called "Hide all windows and focus desktop".

---

