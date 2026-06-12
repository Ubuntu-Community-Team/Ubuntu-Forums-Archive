---
title: "ubuntu on imac"
date: 2010-06-11
forum: Apple Hardware Users
---

### Post by dzon65 on 2010-06-11
I've tried several releases to install on imac G3.All of them failed.(debian ended up with a black screen,9.10,9.04,6.06 all froze)The last I've tried is 8.04 alternate ppc.I managed to get a lxde desktop but running in low graphics.I followed the instructions given here:[http://ubuntuforums.org/showthread.php?t=405934](http://ubuntuforums.org/showthread.php?t=405934)
There are two problems.The first is setting the date(I believe it's necessary todo this first) but I don't have the original keyboard,so  is there another key combination I can use to  do it?The second one is that I can't reconfigure the xorg.conf file.When I do sudo nano /etc/X11/xorg.conf,there's nothing there to configure.When I boot,a small window pops up that ubuntu is running in low graphics because it's unable to find a valid framebuffer device2)failed to open framebufferdevice3)screenss found but none have a usable configuration.When clicked ok,another window pops up giving me three options1)run in low-graphics2)reconfigure graphics3)troubleshoot the error.If I choose to reconfigure,create a new conf,it's impossible to do.I've tried at least ten times now to install and getting tired of it.I'm gonna give it a last try and I hope I don't end up with the same probs.So any help would be welcome;

---

### Post by Iowan on 2010-06-11
Moved to Apple Users.

---

### Post by Frobber on 2010-06-11
Starting with Ubuntu 9.10, xorg.conf has been left out. The reason is detection software is used to sense 'hot' plug devices (usb and video connections).

For older machines, not having 'hot' plug devices, this becomes an issue.

To generate an xorg.conf for your machine:

Key - ctrl+alt+F1 (or 2 through 6), this will put you in virtual terminal mode.

Log in

Type - sudo service gdm stop (this will stop the X server)
Type - sudo Xorg -configure (this should generate an ~/xorg.new)
Type - sudo mv ~/xorg.new /etc/X11/xorg.conf
Type - sudo service gdm start


Type - reboot

I found this at a site by googling "ubuntu xorg.conf"

---

### Post by linuxopjemac on 2010-06-11
or you take a working one [here]("http://mac.linux.be/content/g3-imac-tray-loader-slotloader-all-versions-xorgconf"). I can help you tweak.

---

### Post by dzon65 on 2010-06-11
First of all,major thanks for the replies.Just finished a setup using the 8.04 alternate disc.Now there actually was a xorg.conf file,only,without module settings (so again,nothing to change).
Gonna have another try tomorrow (if I do it now,the imac will be airborn).I've read somewhere that the hour/date has to be set (some bug or something),really can't recall (could be debian though).
I really want to get this thing going cause I don't wanna disappoint the girl I promised to do this.
Kind regards,J.

---

### Post by dzon65 on 2010-06-11
> **linuxopjemac said:**
> or you take a working one [here]("http://mac.linux.be/content/g3-imac-tray-loader-slotloader-all-versions-xorgconf"). I can help you tweak.

Dit jaagt me de muren op.Heb al dozijnen minimals geinstalleerd,maar deze is echt te gek.Heb er al een paar pakketjes cd's doorgedraaid.AAAAArrrrggghhh

---

