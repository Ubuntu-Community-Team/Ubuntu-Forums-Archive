---
title: "Start up script to connect wireless"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2008-01-21
Hi there, im not sure how big of an ask this is, but im wondering if it could be possible to have some kind of script that would do the following for me:

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid "myessid"
sudo iwpriv wlan0 set AuthMode=WPAPSK
sudo iwpriv wlan0 set EncrypType=TKIP
sudo iwpriv wlan0 set WPAPSK="mypword"
sudo dhclient wlan0

so that i dont have to type the above in each time i reboot my pc to connect to the internet, thanks in advance

ps using ralink rt73 usb adapter, installed drivers, kubuntu 7.10

---

### Post by argie on 2008-01-21
Sure, that can be done.

Save the following as wireless-login.sh
```

#! /bin/bash
ifconfig wlan0 down
dhclient -r wlan0
iwconfig wlan0 essid "myessid"
iwpriv wlan0 set AuthMode=WPAPSK
iwpriv wlan0 set EncrypType=TKIP
iwpriv wlan0 set WPAPSK="mypword"
dhclient wlan0

```

Right-click on the script, go to Permissions and set it to be executable.

Now go edit your rc.local file
```

sudo nano /etc/rc.local

```
And put the path to the script in there on the line above 'exit 0'

That should work, but I haven't tried this in ages.

---

