---
title: "Newer Version of Firefox???"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by mengd2002 on 2006-04-17
I installed Ubuntu 5.1 last night.  One thing I've noticed is the ease of installation.  And you don't need a fancy GUI installer interface.  Overall, I am quite pleased.  I do have a question though.

How do I go about installing the 1.5 version of Firefox?  Or newer versions of other software for that matter?  I am new to APT and Synaptic.  If you could answer my post directly or point me to the appropriate documentation, it would be appreciated.  

Don

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=mengd2002]I installed Ubuntu 5.1 last night.  One thing I've noticed is the ease of installation.  And you don't need a fancy GUI installer interface.  Overall, I am quite pleased.  I do have a question though.

How do I go about installing the 1.5 version of Firefox?  Or newer versions of other software for that matter?  I am new to APT and Synaptic.  If you could answer my post directly or point me to the appropriate documentation, it would be appreciated.  

Don[/QUOTE]
Yes automatix to install Firefox 1.5.0.1 and then use "Check for Updates" to install the latest 1.5.0.2 version.

Edit: To install Automatix, type this in terminal. Copy and Paste.

> wget [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
sudo dpkg -i automatix_5.7-3_i386.deb

Once installed start it from Applications > System Tools > Automatix. Then check the things that you want and then hit ok. :)

---

### Post by aysiu on 2006-04-17
Automatix would be great for installing popular codecs and a lot of popular applications.

For installing Firefox, I would use this script, which will give you 1.5.0.2 straightaway:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by majstor on 2006-04-17
[QUOTE=mengd2002]
How do I go about installing the 1.5 version of Firefox?  Or newer versions of other software for that matter?  I am new to APT and Synaptic.  If you could answer my post directly or point me to the appropriate documentation, it would be appreciated.  

Don[/QUOTE]

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by aysiu on 2006-04-17
[QUOTE=majstor][https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)[/QUOTE] The aforementioned script just automates the Wiki tutorial, since the Wiki is essentially just the copying and pasting of commands.

---

### Post by _linux_ on 2006-04-17
Go to [this]("https://wiki.ubuntu.com/FirefoxNewVersion") wiki page.

---

