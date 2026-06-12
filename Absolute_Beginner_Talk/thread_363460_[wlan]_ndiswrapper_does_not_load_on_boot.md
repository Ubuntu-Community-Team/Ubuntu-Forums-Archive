---
title: "[wlan] ndiswrapper does not load on boot"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by c00ch on 2007-02-16
I'm having more troubles  of the wireless variety.

For some strange reason ndiswrapper does not load on boot despite executing

```
sudo ndiswrapper -m
```

a dozen times now. Drivers are all installed okay and working but after each boot I have to call

```
sudo modprobe ndiswrapper
```

followed by

```
sudo dhclient
```

Without the latter bit the wireless adapter would not connect to the AP; dhclient also changes the static IP I have assigned to my wlan adapter.

Anyone has an idea what is going on here? 

P.S.
Perhaps I should mention that I have installed ndiswrapper from source (as described [_here_]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#5_-_Installing_ndiswrapper")) rather than the ubuntu repo as the latest kernel update gave me some grief with the repo-version of ndiswrapper.

---

### Post by dbbolton on 2007-02-17
maybe you'll need to write a shell script with those commands and add it to your start-up programs.

---

### Post by c00ch on 2007-02-17
Okay.

I figured out how to get ndiswrapper to autoload on boot (found the solution [_here_]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#6_-_Autoloading_2"))

```
sudo gedit /etc/modules
```

and add  **ndiswrapper** to the list of modules.

However, my static IP still won't work and I have to use the dhclient to get hooked up to my AP. Funny thing is... I tried 192.168.1.100 as a static IP which wouldn't work but oddly enough dhclient worked - with 192.168.1.100 being my IP assigned by the AP...:confused: 

uh?

---

### Post by dbbolton on 2007-02-17
maybe there was a problem with the dns server in the static configuration.

---

