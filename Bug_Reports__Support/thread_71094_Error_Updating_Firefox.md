---
title: "Error Updating Firefox"
date: 2005-10-02
forum: Bug Reports / Support
---

### Post by SteveF on 2005-10-02
I got the message that Firefox had an update (red update circle on desktop near time).  When I downloaded and installed, I got the following errors:

E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support

Firefox is now broken and won't work.  I had to install epiphany to get to this website.

I was going to uninstall firefox and see if that would help, but that causes synaptic to want to uninstall way too much of the desktop.

Any suggestions?

Thanks,

Steve

---

### Post by Gustav on 2005-10-02
It seems as uninstalling is the way to go :-/
The same thing happend to me, just keep track of the other programs that need to be uninstalled and reinstall them again.

---

### Post by SteveF on 2005-10-03
Is this a problem with:
a) My setup
b) The way the package was built
c) Something inherent in using backports
d) Other

Thanks

Steve

---

