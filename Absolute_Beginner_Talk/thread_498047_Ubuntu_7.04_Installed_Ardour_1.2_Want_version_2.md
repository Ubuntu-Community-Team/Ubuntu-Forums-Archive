---
title: "Ubuntu 7.04 Installed Ardour 1.2 Want version 2"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by jazzman14 on 2007-07-10
I have Ubuntu version 7.04

I installed Ardour 1.2 through synaptic

How can I get version 2

thanks!

---

### Post by jazzman14 on 2007-07-11
bump..anyone?

---

### Post by hackle577 on 2007-07-11
You could uninstall it and [compile the newer version from source]("http://ardour.org/download_full"). Other than that, I don't know, I'm in Windows ATM. :-(

---

### Post by sab0403 on 2007-07-11
You first have to add the Ubuntu Studio repositories:```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update
```This adds the repositories to your sources list, as well as gets the public key to download from them.

Then you have to install Ardour:```
sudo apt-get install ardour
```Hope this helps. :popcorn:

****WARNING****: This will add the low-latency kernel, necessary for "pro-level editing", according to Ubuntu Studio's website. Usually you won't notice the difference, but you should know in case some program(s) don't work and you have to boot into the "regular" kernel - this happened to me with VMWare Server. No biggie really, but just so you know... You can choose between low-latency and generic in the GRUB boot menu.

:guitar:

---

### Post by jazzman14 on 2007-07-11
sweeeeeet

thanks everbody :guitar:

---

