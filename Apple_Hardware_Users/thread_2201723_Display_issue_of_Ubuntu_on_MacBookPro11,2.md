---
title: "Display issue of Ubuntu on MacBookPro11,2"
date: 2014-01-25
forum: Apple Hardware Users
---

### Post by tmsandeep on 2014-01-25
[COLOR=#000000]Can anybody please help me with this? I installed Ubuntu on Mac but I face a weird issue its not being displayed properly on laptop display but with external monitor it is fine.[/COLOR]

---

### Post by tmsandeep on 2014-01-25
Is this something special which am only facing? Has anybody faced or heard of this issue. Please help me.

---

### Post by kris-pypen-i on 2014-01-26
Hello, I had the same ugly screen. Here is the way I managed to install ubuntu 13.10 on my MBP 11,2:

usb stick non-mac
boot from usb, when grub: press "e" and add nomodeset -> press F10 to continue
install ubuntu
restart and boot again in "try ubuntu" and switch to Ctrl+Alt+F1 when booted
apt-get install efibootmgr
sudo efibootmgr -o 0
reboot into real OS and switch to Ctrl+Alt+F1 when booted
apt-get install vim
set GRUB_CMDLINE_LINUX="libata.force=noncq" into /etc/default/grub
reboot into real OS and switch to Ctrl+Alt+F1 when booted
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-rc8-trusty/linux-headers-3.13.0-031300rc8-generic_3.13.0-031300rc8.201401120535_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-rc8-trusty/linux-headers-3.13.0-031300rc8-generic_3.13.0-031300rc8.201401120535_amd64.deb)
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-rc8-trusty/linux-headers-3.13.0-031300rc8_3.13.0-031300rc8.201401120535_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-rc8-trusty/linux-headers-3.13.0-031300rc8_3.13.0-031300rc8.201401120535_all.deb)
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-rc8-trusty/linux-image-3.13.0-031300rc8-generic_3.13.0-031300rc8.201401120535_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-rc8-trusty/linux-image-3.13.0-031300rc8-generic_3.13.0-031300rc8.201401120535_amd64.deb)
sudo dpkg -i *.deb
reboot, now you should have a working ubuntu 13.10 on a MBP 11,2

---

### Post by tmsandeep on 2014-01-26
Thanks a lot Kris it worked :-)

---

### Post by kris-pypen-i on 2014-01-30
I created a wiki page based on the MBP 11,1 page and my experiences: [https://help.ubuntu.com/community/MacBookPro11-2/Saucy](https://help.ubuntu.com/community/MacBookPro11-2/Saucy)

---

