---
title: "HOWTO: Fix random lockups on wireless atheros . MacBook Pro"
date: 2008-08-20
forum: Apple Hardware Users
---

### Post by rytmisk on 2008-08-20
Hi guys and girls. I have been struggling for months with geting my wireless to work flawlessly on my MacBook Pro. I have had a problem called Fifo overrun which makes the wireless network stop working randomly - even if gnome network manager (or other managers, I've tried them all) shows the connection as working. This is on a 64 bit feisty and madwifi, and I'll describe how I managed to make it work. 
This probably only affects those who have the following output from lspci:
```
Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
```

The bug I described above are well documented as a Madwifi bug at [http://madwifi.org/ticket/1017](http://madwifi.org/ticket/1017) and it is marked as fixed. However it still appears with the current cvs which you will be getting if you follow the macbook pro wiki at [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
The solution is to use driver revision 3620 with a patch. This is how I did it:

First I downloaded [http://snapshots.madwifi.org/madwifi-trunk/madwifi-trunk-r3620-20080508.tar.gz](http://snapshots.madwifi.org/madwifi-trunk/madwifi-trunk-r3620-20080508.tar.gz) and untarred it to a folder which will be called  "madwifi-ng-r3550-20080420"

I then downloaded [http://madwifi.org/attachment/ticket/1017/ar5418_dmasize.diff?format=raw](http://madwifi.org/attachment/ticket/1017/ar5418_dmasize.diff?format=raw) to the same folder.

In a terminal I then entered the folder madwifi (cd  madwifi-ng-r3550-20080420) and issued the following command to patch the driver:
```
 patch -p0 < ./ar5418_dmasize.diff 
```

After that it is just to follow the commands described at the macbook wiki page:
```
$ make
$ sudo make install

```
and then 
```

$ sudo modprobe ath_pci
$ sudo modprobe wlan_scan_sta
$ sudo iwpriv ath0 bgscan 0

```

Hope this works and helps someone!

Best regards
Ketil

---

### Post by cyberdork33 on 2008-08-20
you can also try ath9k for your card which will be replacing madwifi. debs are here:
[http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097)

---

### Post by rytmisk on 2008-08-20
I tried it, but for me at least, it seemed to suffer from the same bug. Since I had managed to make it work decently with madwifi and the patch, I decded to uninstall ath9k.  It is really a good project though!

Best Regards
Ketil

---

