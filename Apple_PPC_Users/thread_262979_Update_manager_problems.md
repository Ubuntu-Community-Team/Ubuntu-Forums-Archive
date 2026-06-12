---
title: "Update manager problems"
date: 2006-09-22
forum: Apple PPC Users
---

### Post by spinz8 on 2006-09-22
There  are 04 files to update today and i get this error dialog
The following problems were found in your system:
"E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory"
Any ideas?
Thanks

---

### Post by dumµ on 2006-09-24
(1) Close synaptic, apt-get, and aptitude (if running).

(2) Delete your lock file. In terminal, type

sudo rm /var/cache/apt/archives/lock



(I am sorry not using appropriate formatting, but something doesn't seem to work in my browser...)

---

### Post by spinz8 on 2006-09-24
Noted with thanks.
I have restored the update manager status by typing:
sudo dpkg-reconfigure phigh xserver-xorg
Regards.

---

