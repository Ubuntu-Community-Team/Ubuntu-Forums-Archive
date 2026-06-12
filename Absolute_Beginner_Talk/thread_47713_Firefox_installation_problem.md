---
title: "Firefox installation problem"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by ozzie123 on 2005-07-09
Hello,

I have just added a new repository server as guided in ubuntuguide.org. The problem now is, after I download firefox_1.0.4-1ubuntu3~5.04ubp5_i386.deb via Synaptic update, it shows me this error:


Errors were encountered while processing:
 firefox_1.0.4-1ubuntu3~5.04ubp5_i386.deb

E: /var/cache/apt/archives/firefox_1.0.4-1ubuntu3~5.04ubp5_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package mozilla-firefox
E: /var/cache/apt/archives/firefox-gnome-support_1.0.4-1ubuntu3~5.04ubp5_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/mozgnome.xpt', which is also in package mozilla-firefox-gnome-support

And when I tried to installed it manually from the terminal it shows this:


Unpacking firefox (from firefox_1.0.4-1ubuntu3~5.04ubp5_i386.deb) ...
dpkg: error processing firefox_1.0.4-1ubuntu3~5.04ubp5_i386.deb (--install):
 trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package mozilla-firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)

Can anyone here tell me what's happening?

Thank you
PS: I'm pretty sure that this is a newbie question but if it's not that newbie, please remove it to the appropriate forum.

---

### Post by Williams477 on 2005-07-09
I couldn't get the repository to work either. I just went to the FireFox site and downloaded the package manually then ran the install and it works fine.

---

