---
title: "How to install KMyMoney 0.8.4"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by ccheaton on 2006-08-24
I just wanted to post this here because it took me a while to figure out and I thought it might help others overcome frustration.

There is a problem with the repository version of KMyMoney when you enter investments.  If you add 200 shares of a given stock, it displays that 400 are owned in the account overview.  

Version 0.8.4 does not do that.  However, if you go to Sourceforge and try to download 0.8.4 (the .deb) it claims a dependency on a file that has since been updated for security purposes and therefore, you cannot install it.

Based on a Google Translation of this French Ubuntu forum post:
[http://forum.ubuntu-fr.org/viewtopic.php?pid=443999](http://forum.ubuntu-fr.org/viewtopic.php?pid=443999)

I found a version of 0.8.4 packaged for Ubuntu on a German ubuntu repository site.  You can download the .deb (that will install without the impossible dependency) here:
[http://ubuntu-debs.de/app/kmymoney/](http://ubuntu-debs.de/app/kmymoney/)

Just right click on it and select 'Open with GDebi Package Installer' and you should be good to go, assuming you have the other dependencies installed.  If you upgrade to this, I would recommend removing your prior version before installing this one.  

I can confirm that the annoying bug mentioned above is fixed is this .deb.

---

### Post by msak007 on 2006-08-24
I can't say I've had the same problem, but I compiled KMyMoney from source because I also had a problem with the repo version - it didn't have the DirectConnect OFX online banking backend compiled with it so it made it useless for me. I compiled it from source along with its other dependencies, and it's working great. Does that deb you linked to include that feature?

---

