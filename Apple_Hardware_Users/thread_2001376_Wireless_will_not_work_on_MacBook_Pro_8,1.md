---
title: "Wireless will not work on MacBook Pro 8,1"
date: 2012-06-10
forum: Apple Hardware Users
---

### Post by JRodz26 on 2012-06-10
Hi! 
I install Ubuntu via Wubi on a MacBook Pro 8,1. The installation was easy but when I try to connect to the Internet wasn't possible. I tried different ways to make it work but I need help.

Anu suggestions?

Thanks!

---

### Post by SeanEE89 on 2012-06-12
> **JRodz26 said:**
> Hi! 
I install Ubuntu via Wubi on a MacBook Pro 8,1. The installation was easy but when I try to connect to the Internet wasn't possible. I tried different ways to make it work but I need help.

Anu suggestions?

Thanks!

Unfortunately our wireless cards have TERRIBLE support. There are a few fixes to get this running. I'm chiming in for help regarding the same question. A sticky thread would be really helpful with step by step instructions, because I am a newb to the world of Ubuntu. :\

---

### Post by mjuhasz on 2012-06-13
You'll have to install a modified version of b43-fw-cutter and firmware-b43-installer.
You can find both in my ppa: [https://launchpad.net/~mjuhasz/+archive/mac/+packages](https://launchpad.net/~mjuhasz/+archive/mac/+packages)

You can also just download the packages and install them without adding my ppa (which has other packages that you don't need).

Download the following files into an empty directory:

32 bit:

[https://launchpad.net/~mjuhasz/+archive/mac/+files/b43-fwcutter_015-9ppa1_i386.deb](https://launchpad.net/~mjuhasz/+archive/mac/+files/b43-fwcutter_015-9ppa1_i386.deb)
[https://launchpad.net/~mjuhasz/+archive/mac/+files/firmware-b43-installer_015-9ppa1_all.deb](https://launchpad.net/~mjuhasz/+archive/mac/+files/firmware-b43-installer_015-9ppa1_all.deb)

64 bit:
[https://launchpad.net/~mjuhasz/+archive/mac/+files/b43-fwcutter_015-9ppa1_amd64.deb](https://launchpad.net/~mjuhasz/+archive/mac/+files/b43-fwcutter_015-9ppa1_amd64.deb)
[https://launchpad.net/~mjuhasz/+archive/mac/+files/firmware-b43-installer_015-9ppa1_all.deb](https://launchpad.net/~mjuhasz/+archive/mac/+files/firmware-b43-installer_015-9ppa1_all.deb)

Then install these 2 packages: sudo dpkg -i *.deb


If you use suspend then you'll have to reload the driver to make it work after resume:

Create file /etc/pm/config.d/modules with line:

SUSPEND_MODULES="b43 bcma"

---

