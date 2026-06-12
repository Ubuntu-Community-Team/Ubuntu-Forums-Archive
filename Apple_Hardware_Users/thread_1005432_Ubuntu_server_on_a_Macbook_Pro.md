---
title: "Ubuntu server on a Macbook Pro"
date: 2008-12-08
forum: Apple Hardware Users
---

### Post by S.G. on 2008-12-08
Hello,

I've just installed Ubuntu 8.10 server (AMD64) on a partition of my Macbook Pro (Intel, Core 2 Duo). Bootcamp wouldn't recognize it, so I had to install rEFIt...

Nevertheless, the problem is the net. I'm conected via wifi, and Ubuntu server didn't get it during installation. So now it's off. Does anyone know how to configure it from terminal? I'm not too used to terminal... and there is nothing else in the server version.

Or, can I install from a cd or USB gnome desktop somehow?

Thanks in advance,

S.

---

### Post by lovelyvik293 on 2008-12-08
If you are not good with terminal it's bit hard but no problem i will help you.
First of all you have atheros wifi card.So you have to install the madwifi driver.
Use this procedure:-
> 
 sudo aptitude install build-essential
 wget -c [http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz](http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz)
 tar -zxf madwifi-trunk-current.tar.gz
 cd madwifi-ng-*
 make
 sudo make install
 sudo modprobe ath_pci
 sudo modprobe wlan_scan_sta

You need to have wired link for this.
Or you can manually download the driver from site and then follow the procedure.(Don't use the wget line in this case)

---

### Post by S.G. on 2008-12-08
Thanks a lot lovelyvik239, I'm going to try that right now!

---

### Post by cyberdork33 on 2008-12-08
There is more than one type of card in Macbook Pros.

Please see the "Before you post" link in my signature to determine your mac version and find the appropriate documentation.

---

