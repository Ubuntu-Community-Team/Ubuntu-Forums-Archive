---
title: "Dual booting with a mac mini"
date: 2015-12-11
forum: Apple Hardware Users
---

### Post by hackarre on 2015-12-11
I wanted to re purpose a mac mini as an Ubuntu Server, so far it has been working great except for booting. I previously ran the system with an older version of OSX and Ubuntu 14.04 with the same setup and it always worked fine.

To accomplish the dual boot I simply installed the new OSX El Capitan and made a partition for Ubuntu during the installation. I logged into the new system and installed Refind. Then I installed Ubuntu Server and rebooting sends me to Grub, which is what I want.

The problem comes when I disconnect the keyboard, if the mac doesn't detect one it'll boot to OSX an launch a gui to help you connect a wireless one.
As soon as I add a keyboard the boot order changes back to grub first.

Maybe Apple added this new functionality recently and messes with the boot up process? :???:


[EDIT]: The problem was related to grub not being properly installed. The issue was weird because sometimes the machine would boot to Ubuntu and others (most) to OSX. I solved it by installing and running disk-repair on a live cd. It now boots to grub everytime.

---

