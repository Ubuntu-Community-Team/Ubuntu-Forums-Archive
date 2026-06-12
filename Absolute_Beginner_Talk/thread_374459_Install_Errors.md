---
title: "Install Errors"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Aurora Borealis on 2007-03-02
Well, My system is working with the new installation-good-but I do have a few errors. Things that coulsdn' tbe retrieved from the server. I did a copy to npaste, but the window then announced new updates and I couldn't paste. But then after it checked it found more updates which couldn't be authenticated. These I have:

automatix2 (version 1.1-2.13-6.10edgy_i386) will be upgraded to version 1.1-2.16-6.10edgy_i386
bind9-host (version 1:9.3.2-2ubuntu3) will be upgraded to version 1:9.3.2-2ubuntu3.1
dnsutils (version 1:9.3.2-2ubuntu3) will be upgraded to version 1:9.3.2-2ubuntu3.1
firefox (version 2.0+0dfsg-0ubuntu3) will be upgraded to version 2.0.0.2+0dfsg-0ubuntu0.6.10
firefox-gnome-support (version 2.0+0dfsg-0ubuntu3) will be upgraded to version 2.0.0.2+0dfsg-0ubuntu0.6.10
kdelibs-data (version 4:3.5.5-0ubuntu3) will be upgraded to version 4:3.5.5-0ubuntu3.1
kdelibs4c2a (version 4:3.5.5-0ubuntu3) will be upgraded to version 4:3.5.5-0ubuntu3.1
libbind9-0 (version 1:9.3.2-2ubuntu3) will be upgraded to version 1:9.3.2-2ubuntu3.1
libdns21 (version 1:9.3.2-2ubuntu3) will be upgraded to version 1:9.3.2-2ubuntu3.1
libgtk2.0-0 (version 2.10.6-0ubuntu3) will be upgraded to version 2.10.6-0ubuntu3.1
libgtk2.0-bin (version 2.10.6-0ubuntu3) will be upgraded to version 2.10.6-0ubuntu3.1
libgtk2.0-common (version 2.10.6-0ubuntu3) will be upgraded to version 2.10.6-0ubuntu3.1
libisc11 (version 1:9.3.2-2ubuntu3) will be upgraded to version 1:9.3.2-2ubuntu3.1
libisccc0 (version 1:9.3.2-2ubuntu3) will be upgraded to version 1:9.3.2-2ubuntu3.1
libisccfg1 (version 1:9.3.2-2ubuntu3) will be upgraded to version 1:9.3.2-2ubuntu3.1
liblwres9 (version 1:9.3.2-2ubuntu3) will be upgraded to version 1:9.3.2-2ubuntu3.1
libmagick9 (version 7:6.2.4.5.dfsg1-0.10) will be upgraded to version 7:6.2.4.5.dfsg1-0.10ubuntu0.2
libnspr4 (version 2:1.firefox2.0+0dfsg-0ubuntu3) will be upgraded to version 2:1.firefox2.0.0.2+0dfsg-0ubuntu0.6.10
libnss3 (version 2:1.firefox2.0+0dfsg-0ubuntu3) will be upgraded to version 2:1.firefox2.0.0.2+0dfsg-0ubuntu0.6.10
libsmbclient (version 3.0.22-1ubuntu4) will be upgraded to version 3.0.22-1ubuntu4.1
linux-generic (version 2.6.17.10) will be upgraded to version 2.6.17.11
linux-headers-generic (version 2.6.17.10) will be upgraded to version 2.6.17.11
linux-image-generic (version 2.6.17.10) will be upgraded to version 2.6.17.11
linux-libc-dev (version 2.6.17.1-10.34) will be upgraded to version 2.6.17.1-11.35
linux-restricted-modules-common (version 2.6.17.5-11) will be upgraded to version 2.6.17.7-11.2
linux-restricted-modules-generic (version 2.6.17.10) will be upgraded to version 2.6.17.11
openoffice.org-common (version 2.0.4-0ubuntu2) will be upgraded to version 2.0.4-0ubuntu4
openoffice.org-style-default (version 2.0.4-0ubuntu2) will be upgraded to version 2.0.4-0ubuntu4
openoffice.org-style-industrial (version 2.0.4-0ubuntu2) will be upgraded to version 2.0.4-0ubuntu4
samba-common (version 3.0.22-1ubuntu4) will be upgraded to version 3.0.22-1ubuntu4.1
slocate (version 3.1-1) will be upgraded to version 3.1-1ubuntu0.1
smbclient (version 3.0.22-1ubuntu4) will be upgraded to version 3.0.22-1ubuntu4.1
wine (version 0.9.30-0ubuntu2~edgy1) will be upgraded to version 0.9.31~winehq0~ubuntu~6.10-1
linux-headers-2.6.17-11 (version 2.6.17.1-11.35) will be installed
linux-headers-2.6.17-11-generic (version 2.6.17.1-11.35) will be installed
linux-image-2.6.17-11-generic (version 2.6.17.1-11.35) will be installed
linux-restricted-modules-2.6.17-11-generic (version 2.6.17.7-11.2) will be installed


And of course, being unauthenticated, there's a warning attending the installation of these. But I'm noticing that these seem to be the items that could not be retrieved. How do I know if it's okay to download?

---

### Post by carlosfocker on 2007-03-19
So are the packages above giving you errors upon updating. I'm not sure what you are trying to ask, srry. Please clarify

---

### Post by DougieFresh4U on 2007-03-19
How about maybe trying **sudo apt-get -f install** then **sudo dpkg --configure -a**

---

### Post by Aurora Borealis on 2007-03-21
Thank you both for your replies. What happens is,  when I receive an update notification and try to update, I get a message saying the updates cannot be authenticated, and downloading them could be a security risk. So I don't install them. But I get notice that they're there each day and I can't remove them from the update menu, either-at least I don't know how. I still have an automatix update from last week that can't be authenticated, so it's still there-I'm not sure how to remove it or why it can't be authenticated.

Edit: it turns out it wasn't just when I installed, but frequently. About a third of the time I get updates.

---

### Post by carlosfocker on 2007-03-22
The problem with automatix I believe is something on there end. There web page is down and I found this post [http://ubuntuforums.org/showthread.php?t=387633.(I](http://ubuntuforums.org/showthread.php?t=387633.(I) could be wrong)

Please type this in a terminal

```
sudo apt-get update
sudo apt-get upgrade
```

Post back if the errors if you receive any.

---

### Post by Aurora Borealis on 2007-03-22
That would explain it. Thank you very much. It took me a while to figure out it was the automatix because when there are several downloads I still get a single general warning. Or maybe there's a way to distinguish and I just don't know how yet. But finally when other updates without automatix came through okay, and it was just the automatix, I finally noticed the pattern and put two and two together. That would explain why when I tried installing the CE 2.1 upgrade I got the general warning at the time of install. It must take a doctoral degree to know all this stuff.

---

### Post by carlosfocker on 2007-03-22
All you need is no life :)

---

### Post by Aurora Borealis on 2007-03-22
Well if that's the case, I should soon be an expert, because I've *had* no life ever since I started liking my computer! :D

---

### Post by carlosfocker on 2007-03-22
join the club

---

