---
title: "Ubuntu wont boot"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by x05 on 2008-03-07
I tried to upgrade, but the only problem is that and it wouldnt work normal. So I held control then alt, and pressed F4. Then I typed in: sudo apt-get disto-upgrade.
I let it do its thing.
Then it was talking about RAID config, i just typed all beacuse it said to do that if i wanted it all to load.
I then reeboted. It now says "XServer Fails to Load" then goes to that dos screen. I then tried typing: sudo dpkg-reonfigure xserver-xorg. Now it says I need to be root. I tried every password I could thing of. No go.
Help me please...
Im starting to think this linux was a bad idea

---

### Post by forestpixie on 2008-03-07
try a bit more information as well - :)

---

### Post by x05 on 2008-03-07
Thats all I have? Is there a root password or something?

---

### Post by forestpixie on 2008-03-07
try booting the recovery mode and do the dpkg reconfigure with -phigh

dpkg-reconfigure -phigh xserver-xorg

shouldn't need sudo in recovery

but I have no idea about raid - so if it's that I can't help :(

---

### Post by x05 on 2008-03-07
W.e. Im done. I've had nothing but problems since the first day of last week. Couldn't get clit installed, so i changed sources.list and then upgraded. Now im here.

---

