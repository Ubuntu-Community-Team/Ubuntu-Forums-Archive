---
title: "Gaim Woes"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by wcbardwell on 2007-06-19
Gaim keeps freezing my machine! It allows me to send one message and halfway through the second, it freezes my desktop. I can still move the cursor, but keystrokes and clicks do nothing. I am forced to reboot by pressing and holding the power button on my machine. I recently did a fresh re-installation of 7.04 and it didn't give me problems before I had done so. Any ideas?

Dell
3.4 HT P4
1GB RAM
120 GB EIDE HD

---

### Post by misconfiguration on 2007-06-19
I've not heard of that, what are the specs of your machine? 

This is what I'd do:

sudo apt-get remove --purge *gaim

If you currently already have the newest version *pidgin* do this..

sudo apt-get remove --purge *pidgin

after that's done try to reinstall the app.

wget [http://vicox.net/ubuntu/pidgin_2.0.0beta7devel.vicox-1_i386.deb](http://vicox.net/ubuntu/pidgin_2.0.0beta7devel.vicox-1_i386.deb)

Install the .deb package using the following command

sudo dpkg -i pidgin_2.0.0beta7devel.vicox-1_i386.deb

This will install all the required packages for pidgin.

If you want to open pidgin go to Applications—>Internet—>Pidgin Instant Messanger

---

### Post by Alex&amp;Linux on 2007-06-19
Thats a tough one!
I have some problems, though less severe with Gaim as well.
I would probably make sure everything is update using:

apt-get update
apt-get upgrade
apt-get dist-upgrade

Then restart...if there still seems to be a problem, you could perhaps un-install Gaim, and re-install!
Unfortunately I have not the experience to go beyond these simple measures.
I suppose that if you were able to view the output of Gaim, it would be easier to figure out!

Experiencing freezing anywhere else?
Do you use Beryl or another non-metacity window manager?

Saludos!

---

### Post by finer recliner on 2007-06-19
i would uninstall gaim and install the lastest version (renamed to pidgin!)

---

