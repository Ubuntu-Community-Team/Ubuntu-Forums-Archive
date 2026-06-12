---
title: "Wifi (Firmware Missing) Macbook Pro 8,1 (12.04)"
date: 2012-09-19
forum: Apple Hardware Users
---

### Post by bigrunnermaniac on 2012-09-19
I am relatively new too linux and just installed ubuntu onto my computer.  I am currently using a wired connection because the wifi options display I have firmware missing, however, when I open Additional Drivers and it searches, I receive the message "No proprietary drivers found on this system." Anybody have any solutions. I have looked every where.

---

### Post by mjuhasz on 2012-09-20
You can use the firmware installer [from my ppa]("https://launchpad.net/~mjuhasz/+archive/mac"). It is updated to extract the firmware for the wi-fi card in your MacBook Pro. I suggest you don't add my ppa since it contains other packages as well but just download what you need and install.

If you have a 32 bit installation, download:

[https://launchpad.net/~mjuhasz/+archive/mac/+files/b43-fwcutter_015-9ppa1_i386.deb](https://launchpad.net/~mjuhasz/+archive/mac/+files/b43-fwcutter_015-9ppa1_i386.deb)
[https://launchpad.net/~mjuhasz/+archive/mac/+files/firmware-b43-installer_015-9ppa1_all.deb](https://launchpad.net/~mjuhasz/+archive/mac/+files/firmware-b43-installer_015-9ppa1_all.deb)

or, if you have a 64 bit installation, download:

[https://launchpad.net/~mjuhasz/+archive/mac/+files/b43-fwcutter_015-9ppa1_amd64.deb](https://launchpad.net/~mjuhasz/+archive/mac/+files/b43-fwcutter_015-9ppa1_amd64.deb)
[https://launchpad.net/~mjuhasz/+archive/mac/+files/firmware-b43-installer_015-9ppa1_all.deb](https://launchpad.net/~mjuhasz/+archive/mac/+files/firmware-b43-installer_015-9ppa1_all.deb)

You can then install these two packages either by double-clicking (Software Center will open up) or from command-line:

sudo dpkg -i b43-fwcutter* firmware-b43-installer_015-9ppa1_all.deb

---

### Post by skipperczt on 2012-09-23
Install the package linux-firmware-nonfree and reboot.

---

