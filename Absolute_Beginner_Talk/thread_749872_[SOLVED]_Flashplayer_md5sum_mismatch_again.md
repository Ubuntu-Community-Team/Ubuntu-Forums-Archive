---
title: "[SOLVED] Flashplayer md5sum mismatch again?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by piratesmack on 2008-04-08
Anyone else experiencing this?

I was able to install flashplayer fine last night

---

### Post by FuturePilot on 2008-04-08
Looks like they released a new version 9.0.124.0 . Here we go again. :roll:

---

### Post by piratesmack on 2008-04-08
> **FuturePilot said:**
> Looks like they released a new version 9.0.124.0 . Here we go again. :roll:

aw man

I hated this bug
](*,)

Anyone got a fix?

should I just download the flashplayer directly from adobe?

---

### Post by piratesmack on 2008-04-09
*bump

---

### Post by DMK62 on 2008-04-09
from my previous post

It appears that the issues with the flashplugin-nonfree is back again. It's the md5sum error and message that the plugin is NOT installed. I checked launchpad and its currently confirmed.

[https://bugs.launchpad.net/ubuntu/+s...ee/+bug/173890](https://bugs.launchpad.net/ubuntu/+s...ee/+bug/173890)

From a recent post by Saïvann Carignan

Setting back to confirmed in Gutsy and Hardy, md5sums mismatch happens again because of new 9.0.124.0 release.

Let's hope this one gets fixed asap.

Dale

---

### Post by piratesmack on 2008-04-09
This is how I got flash installed:
1. Remove the supposedly installed flashplayer
```
sudo apt-get remove --purge flashplugin-nonfree
```
2. Download flashplayer directly from Adobe to your desktop:
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
3. Open a terminal and run each command one at a time:
```
cd Desktop
tar -xzvf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux
sudo su
./flashplayer-installer
```
4. Press ENTER to begin installation
5. Exit any web browsers you have running
6. When it asks for the installation directory, type:
```
/usr/lib/firefox
```

Hope this helps

---

### Post by 5735guy on 2008-04-09
Many thanks brilliant :):):)

One question why does this problem happen upon a new release ?

---

### Post by philinux on 2008-04-09
Must be a gutsy thing. New version working fine on Hardy. Except it crashes firefox now and then. Testing Testing .......

---

### Post by Stettin on 2008-04-14
I don't know if this makes any difference, but I needed to add the trailing / after firefox, was running Xubuntu 7.10

---

### Post by piratesmack on 2008-04-20
> **5735guy said:**
> Many thanks brilliant :):):)

One question why does this problem happen upon a new release ?

Yeah I think so. The problem seems to be fixed now, so hopefully Adobe doesn't screw it up again when they release their next version of flashplayer

---

