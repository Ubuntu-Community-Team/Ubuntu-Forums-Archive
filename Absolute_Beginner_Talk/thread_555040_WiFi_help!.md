---
title: "WiFi help!"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Arkasai on 2007-09-19
The WiFi network at my university is wicked fast, but very unreliable.  I know it's not a specific hardware issue, because others experience rather frequent disconnects as well.  My problem arises from Ubuntu's network manager not wanting to reconnect to my school's network after several disconnects.  Even if the network manager detects the network, it will attempt to connect for about a second....then stop.  Till now I've been fixing this by rebooting.  Is there a way around this?

---

### Post by jamvegan on 2007-09-19
Though I've never had that specific issue, I have had problems with Network Manager and wifi.  I installed and use wifi-radar, which I have found to be much more robust.  I've never had trouble connecting to any network with it--secured or unsecured.

---

### Post by Arkasai on 2007-09-19
Yeah, I've been using WiFi radar too.  Though that doesn't seem to help much, I'll be able to reconnect maybe once or twice more after network manager stops working.

---

### Post by HermanAB on 2007-09-19
Hmm, is it network manager that stops working, or is it your WiFi adaptor that stops working?

Try uninstalling the WiFi driver to force the system to reset the WiFi device and then re-load the driver:
$ sudo lsmod (to figure out what is the driver name)
$ sudo rmmod drivername (removes driver and forces the WiFi adaptor off)
$ sudo modprobe drivername (turns WiFi adaptor on and re-load the driver)

Now run WiFi radar or whatever again and life should be good - well, should... ;)

Cheers,

H.

---

### Post by Arkasai on 2007-09-20
sudo lsmod shows me "wlan_scan_sta" and "wlan" in the list, which one do you think I should uninstall/reinstall?

Also, will I run the risk of bricking my WLAN by doing this?

---

### Post by mazor on 2007-09-30
I have the same problem with my Toshiba Portege R200. The Network manager will connect to wireless networks, but every now and then disconnect, and require reconnecting. Quite strange considering I am less than 5 metres from the Access point. 

Signal strength is stuck to max 50%, which I find a bit strange, where in Windows I get full strength.

Also in Windows, I do not get the disconnection problems found using network manager in Ubuntu 7.04.

MAzor

---

