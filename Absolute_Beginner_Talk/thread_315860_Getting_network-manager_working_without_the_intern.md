---
title: "Getting network-manager working without the internet"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by crazybrit4967 on 2006-12-09
In my epic quest to connect to my wireless network in Edgy, I've made it to the point where I have installed the necessary driver with ndiswrapper, but I still can't connect using ifup.  So, I decided to try and see if connecting with network-manager would work.  I downloaded the latest source tarball from [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/), extracted the archive, and ran ./configure.  A bunch of stuff happens, and then it stops and it says I don't have version something point something  of wireless-tools (sorry, I can't post the exact right now, as I'm using windows so I can connect to the internet).  Does anyone know what to do next? - eg where/how to download the latest version, or how to modify the configuration file to let me install it w/o the latest wireless-tools version?  Or maybe downloading an older version of network-manager would do?  Anyway, thanks for any help you can give me!

---

### Post by ciscosurfer on 2006-12-09
You can grab network manager from the repos.

If you are using KDE```
sudo aptitude update && sudo aptitude install knetworkmanager
```If you are using GNOME```
sudo aptitude update && sudo aptitude install network-manager-gnome
```If you really want to install from source, then first you should download build-essential and checkinstall (use instaed of make install -- it will create a .deb package so management of said package becomes as easy as maintaining packages that you install via apt)```
sudo aptitude update && sudo aptitude install build-essential checkinstall
```Then, download and extract the tarball or gunzipped file ([http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/NetworkManager-0.6.4.tar.bz2](http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/NetworkManager-0.6.4.tar.bz2)) to a directory of your choice, like you did before, and run the following commands```
./configure
make
sudo checkinstall -D
```You can also find a list of supported wireless hardware here: [http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware)

---

### Post by crazybrit4967 on 2006-12-09
> **ciscosurfer said:**
> You can grab network manager from the repos.

If you are using KDE```
sudo aptitude update && sudo aptitude install knetworkmanager
```If you are using GNOME```
sudo aptitude update && sudo aptitude install network-manager-gnome
```If you really want to install from source, then first you should download build-essential and checkinstall (use instaed of make install -- it will create a .deb package so management of said package becomes as easy as maintaining packages that you install via apt)```
sudo aptitude update && sudo aptitude install build-essential checkinstall
```Then, download and extract the tarball or gunzipped file ([http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/NetworkManager-0.6.4.tar.bz2](http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/NetworkManager-0.6.4.tar.bz2)) to a directory of your choice, like you did before, and run the following commands```
./configure
make
sudo checkinstall -D
```
Yeah, I know al that; I just don't have the internet up in ubuntu so I can't download the packages.  I was compiling from source so I could download the tarball on another computer and transfer it via flash drive.

---

### Post by mcduck on 2006-12-10
You could just run this on the machine to get a list of net addresses for all packages needed, and then go to [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and download the deb packages..

```
sudo apt-get --print-uris install network-manager-gnome
```

---

### Post by David Corrales on 2006-12-10
I should note that after downloading, you can just copy them to /var/cache/apt/archives and run apt-get. It'll automatically look for them in that folder before attempting to download them.

---

