---
title: "do proxies stick?"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by lemonij on 2007-02-06
Hello,

I've inherited an installation of breezy-ubuntu, and I'm trying to update it and install a few specialist programs.  I've been using debian for a few years, but this is the first time I've touched ubuntu.

My problem is this: previously, the computer has been used on a network which requires a proxy server.  I have disabled this via the system/preferences/network proxy menu, so that I now have a direct connection.  This seems to work well enough for firefox, for example.  

However, when I run 
$sudo aptitude update 
I fail to update anything (0kB download), I get messages saying it is connecting to my former proxy server address, and the apt-sources each return something like this:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
     403 forbidden

I've tried several different locations for apt-sources, and the psychocats.net advice for troubleshooting, and to no avail.  sudo apt-get update doesn't work either.

Can anyone suggest how the proxy may have been hardwired into sudo/aptitude/apt, and how I get rid of it?

Thanks for any help,

Lemonij

---

### Post by lemonij on 2007-02-06
Looking elsewhere on this forum, I found the suggestion to look in my /etc/apt.conf file.  Sure enough, it mentioned my proxy, so I deleted that line.

Unfortunately, it *still* doens't work...

---

### Post by lamego on 2007-02-06
Make sure you don't have the http_proxy var defined...
They only stick when they are defined at some configuration file/variable which is used by the application :)

---

### Post by lemonij on 2007-02-06
Hello,

I don't think I have an http_proxy variable defined, but only because I can't find one in either $sudo apt-config dump or in the preferences for synaptic.  Is there anywhere else I should be looking?

Thanks again
Lemonij

---

### Post by lemonij on 2007-02-06
code $unset http_proxy

care of emilus elsewhere.

Thanks for the directions!

---

