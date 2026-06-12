---
title: "still no firewall"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by skiddly on 2007-02-23
[SIZE="5"][/SIZE]Well after much trouble firestarter will still not work my modem is connected by usb as mentioned in earlier post could this be the prob and is there a fix for this (other than using ethernet)if i can not get this function to work might have to take ubuntu out cos im worried about safety i know its better than windows anyway but there is always someone who will work a way out how to get at your pc how do i uninstall firestarter so i can try and reinstall see if that works thanks for your patience i cant help feeling realy thick at this moment

---

### Post by frodon on 2007-02-23
First of all if you don't run services you don't need a firewall on linux except if you are paranoiac,  it's really different from windows where having a firewall is vital.

Now firestarter is a frontend to iptables which is the most used language to configure netfilter which is the firewall embedded in all linux 2.4 and 2.6 kernel series.
So you don't need firestarter to have a firewall, there's plenty of scripts/frontend to configure an iptables script or you can even write your own iptables script :
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

---

