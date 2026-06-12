---
title: "How to (easily) roll back system changes?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-11-04
As I understand it, I could do this to remove packages that I do not want/is causing me problems;
> To Purge or remove applications:

sudo apt-get remove --purge tor privox ( or xxx xxxxxx )


sudo apt-get remove norton  this removes norton, but keeps your settings.


sudo apt-get remove --purge norton  this will completely remove norton, including config files. 

Is this the best way to go about this? What about system/other updates that cause a problem? How do I "back out" of those? Is there anything avail. like Windows "System restore" yet? If my pc wouldn't boot, or I run into start up problems, I am really foggy on how to go about troubleshooting...

:popcorn:

---

### Post by HermanAB on 2007-11-04
Hmm, some general tips that may save you some hair:
1. Don't install windowslike anti-virus cruft.  Unless you are serving email for Windows users, you don't need it.  If you *really* do need it, use spamassassin and clamav.
2. Don't uninstall stuff.  Linux package managers are good at managing dependencies for installing stuff, but the reverse is frequently not a good idea.
3. Use RCS to manage configuration files in /etc, as described here: [http://www.aeronetworks.ca/rcs-howto.html](http://www.aeronetworks.ca/rcs-howto.html)

Cheers,

Herman

---

### Post by discmaster on 2007-11-04
Should I apply updates regularly as they become available? I see the update manager is set to "daily" by default. Is that the same thing as "sudo apt-get update"?

I thought I remember reading somewhere that it is not a good idea to install all the updates, kind of like in Windows, because some updates may break things, etc...

---

### Post by rsambuca on 2007-11-04
> **HermanAB said:**
> Hmm, some general tips that may save you some hair:
1. Don't install windowslike anti-virus cruft.  Unless you are serving email for Windows users, you don't need it.  If you *really* do need it, use spamassassin and clamav.
2. Don't uninstall stuff.  Linux package managers are good at managing dependencies for installing stuff, but the reverse is frequently not a good idea.
3. Use RCS to manage configuration files in /etc, as described here: [http://www.aeronetworks.ca/rcs-howto.html](http://www.aeronetworks.ca/rcs-howto.html)

Cheers,

Herman
Wow, I really have to disagree with number 2.  Apt-get and synaptic are some of the best in the biz when it comes to keeping track of dependencies.  That point is simply based on outdated information.

---

### Post by rsambuca on 2007-11-04
> **discmaster said:**
> Should I apply updates regularly as they become available? I see the update manager is set to "daily" by default. Is that the same thing as "sudo apt-get update"?

I thought I remember reading somewhere that it is not a good idea to install all the updates, kind of like in Windows, because some updates may break things, etc...

Most of the updates are pretty hassle-free, although there has been the odd one in the past that borks a few things.

---

