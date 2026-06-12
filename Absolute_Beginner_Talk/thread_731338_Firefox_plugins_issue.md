---
title: "Firefox plugins issue"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by ThewhiteLynx on 2008-03-21
When I go to websites and it comes up with a white box instead of  a picture saying a plugin was missing, and then when I tried to download the the plug9in, Adobe Flash PLayer, its comes up with this when I have it selected to install: Can not find 'flashplugin-nonfree'

---

### Post by (((X))) on 2008-03-21
Your software-repositories may be outdated.
Make sure you installed flashplugin-nonfree
sudo apt-get update
sudo apt-get install flashplugin-nonfree

---

### Post by philinux on 2008-03-21
[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)

this will sort you out.

---

### Post by Doctor Debian on 2008-03-21
Although Phil's solution works, I recommend saving yourself hassle in the future by enabling the restricted repository. Go to System / Administration / Software Sources, and check off restricted and multiverse options. When you press close, let it reload and you're set :) .

Doc Deb

---

### Post by ThewhiteLynx on 2008-03-21
That last one seems to have fixed it completely ^_^ thank you for the fix

---

