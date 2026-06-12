---
title: "Upgrade to Gutsy"
date: 2007-10-18
forum: Apple PPC Users
---

### Post by megabenman on 2007-10-18
I have an iMac G5 in a dual boot with Mac OS X 10.4.9 and Kubuntu Feisty.  I'm not sure how to upgrade to Gutsy.  Can someone give me instructions how to do it?

Also, this is Kubuntu, not Ubuntu.

---

### Post by Stemp on 2007-10-18
[https://help.ubuntu.com/community/GutsyUpgrades?highlight=%28gutsy%29#head-3692aaaed415e3427f54ec62dd8659474516b525](https://help.ubuntu.com/community/GutsyUpgrades?highlight=%28gutsy%29#head-3692aaaed415e3427f54ec62dd8659474516b525)

Is it what you're looking for ?

---

### Post by jellisii on 2007-10-18
I'm not shure where to put this.. but when I ran the update manager, the machine now boots to a busybox shell, and has no /dev/hd* or /dev/sd* devices listed...  I can only assume that something happened to the IDE driver for my G4 flatscreen iMac.  I tried it twice to ensure that the problem was valid:  First just editing the the sources list and doing an apt-get dist-upgrade, and second from the desktop as described by the link above.  

This is a major show stopper. I am fortunate that I only had the machine running a week, so I didn't have anything I couldn't replace on it.  There are others that may attempt the same thing that may have larger problems, however.  I'll post more if/when I figure out what I need to do to get this rolling.

Edit 1:  I have found that if you boot and manually select "old" from the yaboot selection, the machine will boot.  It did not bring up my network interfaces as expected, however.

Edit 2:  Apparently the problem lies in the initrd.img and boot kernel.  Booting from the old files works.  My network configuration was broken upon reboot, however.  I had to manually edit the interfaces.conf file to get my network card to light on boot.  

Network manager takes 100% CPU on boot.  The only way to fix it is to kill -9.  HUP does not work.

---

