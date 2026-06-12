---
title: "Howto: Convert Debian/XFCE to LMDE/XFCE"
date: 2012-05-05
forum: Any Other OS
---

### Post by hzFVOW00pw on 2012-05-05
I just converted Debian Testing (Wheezy) XFCE to Linux Mint Debian Edition XFCE. It's a rather simple procedure.

I have no problems with Wheezy, on the contrary, it is fabulous. But I need to upgrade the systems of some Ubuntu Lucid users. I've been playing around with Precise/Unity for a a few months now and ultimately decided it is still not mature and contains too much commercial bloat. What's more I am tired of reinstalling Ubuntu releases on a number of computers every few years. So I decided to upgrade those computers to LMDE, because it is a rolling distro and makes use of upgrade packs (In Wheezy upgrading is too much for the n00b). But it also means I have to run LMDE on my own computer, because I change apt-configuration and other configuration now and then and ssh/rsync it to the other boxes (yes, I could do that in virtulabox too).

Here's how to do it:

Change your /etc/apt/sources.list. Delete the debian repos and add the following mint repos:

```
deb http://packages.linuxmint.com/ debian main upstream import backport
deb http://debian.linuxmint.com/latest/ testing main contrib non-free
deb http://debian.linuxmint.com/latest/security/ testing/updates main contrib non-free
deb http://debian.linuxmint.com/latest/multimedia/ testing main non-free
```


Create an /etc/apt/preferences file with the following content:

```

Package: *
Pin: release o=linuxmint
Pin-Priority: 700

Package: *
Pin: origin packages.linuxmint.com
Pin-Priority: 700

Package: *
Pin: release o=Debian
Pin-Priority: 500
```

Modify /etc/lsb-release to look like this:

```
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=1
DISTRIB_CODENAME=debian
DISTRIB_DESCRIPTION="Linux Mint Xfce Edition"
```

Update the package database, install the linuxmint keyring and mint packages (I use sudo but you can use "su -" of course):

```
sudo apt-get update
sudo apt-get install linuxmint-keyring
sudo apt-get update
sudo apt-get install --reinstall synaptic
sudo apt-get install mint-artwork-debian mint-artwork-xfce mint-backgrounds-debian mint-backgrounds-xfce mint-common mint-info-xfce mint-translations mint-x-icons mint-x-theme mintconfig-xfce mintdesktop-xfce mintsystem mintupdate-debian python-webkit
```
(mintupdate-debian needs python webkit)


Then fire up synaptic and search for 'mint' to see if there's more Mintstuff that you might want to install. The Mint software center is called mintinstall. The ubuntu based software-center doesn't seem to work on LMDE (ImportError: No module named LinuxMint).

Wheezy has some slightly newer libraries than LMDE. During upgrades you might encounter broken packages that depend on older libraries. If that happens try to uninstall such a libary and reinstall it. It will reinstall the older LMDE version.

---

