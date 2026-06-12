---
title: "[SOLVED] MBP wireless with Gutsy?"
date: 2007-10-21
forum: Apple Intel Users
---

### Post by MichaelSwengel on 2007-10-21
Has anyone been able to get wireless networking for the newest Macbook Pros setup on 7.1 Gutsy? I'm new to Linux, and I'm just wondering. If so, how did you do it?

---

### Post by alephsmith on 2007-10-21
[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)

The snap shot listed there worked for me.

---

### Post by ajtudor on 2007-10-21
This worked for me.  Open Terminal and issue these:

sudo apt-get install build-essential

wget [http://snapshots.madwifi.org/madwifi-ng-current.tar.gz](http://snapshots.madwifi.org/madwifi-ng-current.tar.gz)

tar zxvf madwifi [tab]

cd madwifi [tab]

make

sudo make install

---

### Post by MichaelSwengel on 2007-10-21
Great! Thanks, guys! My wireless is now working 100% :D Now I have internet anywhere on my school's campus!! Thanks again!

---

