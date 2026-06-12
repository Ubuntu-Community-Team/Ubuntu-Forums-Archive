---
title: "Installing/updating without Internet?"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by brashquido on 2006-08-30
Hi All,

I am new to Linux and have just setup a few Ubuntu 6.06 systems for friends who are just getting into computing. However I have struck a problem I never considered before, which is these friends don't have Internet access. So my questions are;

1) How do I get the packages they want and burn them to CD?

2) Once on CD, how do I install them?

---

### Post by Bachstelze on 2006-08-30
To download packages, go tp [http://packages.ubuntu.com](http://packages.ubuntu.com) and search for the packages you want, then run the command *sudo dpkg -i filename.deb* to install. But you'll have to manage packages dependencies manually, which can quickly become really complicated. I recommend you get them Debian, it has 14 CDs full of packages instalable with a simple apt-get.

---

### Post by PPAAUULL on 2006-08-30
I guess you could look around for the DEBs you need then just burn a data CD. Next just unpack them and install them like you would a regular downloaded DEB that would be on your desktop (right click, then install somewhere in there.).

---

### Post by brashquido on 2006-08-30
Ohh, manual dependencies sounds ugly, especially with my familiarity with Ubuntu. If that is the only way, then I might just tell them it can't be done until they get the Internet. Problem is these friends live several hundred km's away, and I was kind of hoping that I could burn them a couple of CD's to send them in the mail with some instructions on how to install it.

---

### Post by PPAAUULL on 2006-08-30
Ya that is a bummer. Just tell them to wait till they get internet. I wouldn't want to break there system when you can't go out there and fix it.

---

### Post by VirtuAlex on 2006-08-30
you can try to follow this howto:
[http://cargol.net/~ramon/ubuntu-dvd-en]("http://cargol.net/~ramon/ubuntu-dvd-en")

---

### Post by bruce89 on 2006-08-30
Synaptic has a download script creation utility, but you need the up-to-date archive listing for it to be useful.

You can do this if you have another Ubuntu machine that has an internet connection:
```
sudo apt-get clean
sudo apt-get -d <package you want>
```
Collect all the *.deb files in /var/cache/apt, and install them manually on the other machine.

---

