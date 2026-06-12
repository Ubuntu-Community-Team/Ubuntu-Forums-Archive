---
title: "wifi stopped working on a mbp 5,5 running karmic"
date: 2010-02-07
forum: Apple Hardware Users
---

### Post by confuciusquinn on 2010-02-07
I was attempting to get my sound to work and followed all the instructions found here: [https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Sound](https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Sound) and in the end still no sound, and now i don't have wifi either. Any ideas?

---

### Post by linuxopjemac on 2010-02-08
I would remove those backports...

sudo apt-get remove linux-backports-modules-alsa-karmic-generic

---

