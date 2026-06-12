---
title: "Ubuntu Studio Feisty install failure"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by jrlii on 2007-10-07
I'm trying to install Ubuntu Studio over an existing Feisty installation.

I followed the instructions, but there were problems downloading a couple packages. (it took ten or twelve hours over dialup) I re-ran the apt-get and it downloaded a large package that seemed to be associated with video editing and the install process ran, but there was a problem with Ardour. I tried the apt-get as the error message suggested, without success.

I tried installing Ardour with Synaptic which failed with this message:

E: /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb: trying to overwrite `/usr/share/locale/de_DE/LC_MESSAGES/gtk_ardour.mo', which is also in package ardour-gtk

Any notions as to what I need to do? Uninstall Ardour and try it again? 

Thanke in advance.

---

### Post by jrlii on 2007-10-07
Uninstalling Ubuntu Studio Audio, then re-installing it seems to have done the trick.

---

