---
title: "Query regarding Synaptic Package Manager"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by deviantcynic on 2007-10-20
Can I install pptp package for network manager (network-manager-pptp) via synaptic package manager without connecting to Internet???

I am about to use, Ubuntu 7.10, InshAllah, and I will not be able to connect to the internet until i have the vpn client... So please help...

---

### Post by rohan000 on 2007-10-21
Yes, it's in the instal disc image.

---

### Post by justinmiller87 on 2007-10-21
> **deviantcynic said:**
> Can I install pptp package for network manager (network-manager-pptp) via synaptic package manager without connecting to Internet???

I am about to use, Ubuntu 7.10, InshAllah, and I will not be able to connect to the internet until i have the vpn client... So please help...

Put your install CD in the drive, then go to terminal and type
```
sudo apt-get install network-manager-pptp
```

If it says it can't be found, then go to [http://packages.ubuntu.com/gutsy/net/network-manager-pptp](http://packages.ubuntu.com/gutsy/net/network-manager-pptp) to download it manually and copy it over on a flash drive or other means. It has a bunch of dependencies, so you might want to download those too, or just bring it back to the Gutsy system, then do a "dpkg --info 0.6.5+svnhead2574-0ubuntu1.deb" to see what your system specifically needs.

---

