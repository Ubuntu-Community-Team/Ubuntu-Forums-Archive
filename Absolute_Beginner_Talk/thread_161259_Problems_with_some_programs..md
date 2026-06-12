---
title: "Problems with some programs."
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by wat3r on 2006-04-16
Ok, I have some programs that won't work as they should. Hope I can get some help here.

aMSN:
I start the program, and a error message comes up: Unable to get a socket from local host. Check your /etc/hosts file, please.
Here is what the /etc/hosts file says:

127.0.0.1 localhost.localdomain localhost eirik
192.168.0.88 eirik

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Bittornado Client (Or any torrent client, for that matter) just won't start downloading torrents. It doesn't connect to tracker.

Firefox 1.5.0.1:

When I surf pages where Firefox is supposed to stream audio, I am told to install a plugin (This is just with *.wmv), but when I click the "Install plugin.." thingy, it can't find any plugins.

---

### Post by FedeXX on 2006-04-16
Same amsn problem for me...

Edit: Fix found! There is no loopback in ifconfig! :D

```
sudo ifconfig lo 127.0.0.1
```

---

### Post by Mustard on 2006-04-16
For the plugins problem try installing some of the things mentioned on this page dealing with codecs with restrictive licences...

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by wat3r on 2006-04-17
Ok. Thanks for the answers :)

edit: Now aMSN starts, but it says that I have typed in wrong usr and password. I am 100% certain that I have typed in the right password. I am using gmail, can that have anything to do with it?
Also BitTornado still won't download torrents. It still can't connect to tracker.

---

