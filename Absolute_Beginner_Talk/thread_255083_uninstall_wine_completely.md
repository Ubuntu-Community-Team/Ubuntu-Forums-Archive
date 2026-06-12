---
title: "uninstall wine completely"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by jbumgar on 2006-09-10
I decided to upgrade to wine since I've nothing go right wine 0.9 that Ubuntu supplies.

Before I installed it said it not a registered product. Now I have it on there even went back to synaptic and did a comlete uninstall and nothing happened.

I'd just like to get the original version back on and see if will install properly.

---

### Post by timetunnel on 2006-09-11
AFAIK, "completely" uninstalling a package with Synaptics package manager doesn't delete the files created by user interaction.

Therefore, after uninstalling wine, you'll have to clean up manually by deleting the whole hidden ".wine" folder in your home directory ("/home/username/.wine"). Then re-install the wine version you need.

BTW: if you want to use Internet Explorer: it won't run with the version provided by ubuntu or newer versions from the wine homepage (at least in Dapper). I only got it to work properly with this howto:

[http://ubuntuforums.org/showthread.php?t=149585](http://ubuntuforums.org/showthread.php?t=149585)

---

### Post by jbumgar on 2006-09-11
Thank you for your help timetunnel. Its people like you who deserve a lot of credit for helping us noob.

---

