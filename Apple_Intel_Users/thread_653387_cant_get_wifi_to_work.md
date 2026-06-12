---
title: "cant get wifi to work"
date: 2007-12-29
forum: Apple Intel Users
---

### Post by stealthsniper96 on 2007-12-29
i tried these terminal commands

* sudo aptitude install build-essential 
wget [http://snapshots.madwi&#64257;.org/madwi&#64257;...current.tar.gz](http://snapshots.madwi&#64257;.org/madwi&#64257;...current.tar.gz) 
tar -zxvf madwi&#64257;<tab> 
cd madwi&#64257;<tab> 
make 
sudo make install (answer 'r' when asked)

to get wifi but no luck. so then i connected with an ethernet cable and tried the website in there but it gave me the whole "404 cannot be found" deal. how else can i get the drivers?

---

### Post by xoai on 2007-12-30
Are you sure the driver was installed correctly? Did you get any error during the installation? Did you reboot after finishing? If everything's ok just try some command

ifconfig 
to know what your wifi interface is. Usually it's ath0

sudo ifconfig ath0 up
to birng the interface up

iwlist scanning
to scan for wifi signal around

sudo iwconfig ath0 essid "essid_name"
to choose the wifi hotsot you want

sudo dhclient ath0
to get the IP from access point.

Hope you will be success with those things above.

---

### Post by david_edmundson on 2007-12-30
The URL should be:
[http://snapshots.madwifi.org/madwifi-ng-current.tar.gz](http://snapshots.madwifi.org/madwifi-ng-current.tar.gz)

Yours has got truncated at some point.

---

### Post by alpinesatan on 2007-12-30
i tried sorting mine out for days, read my post
[http://ubuntuforums.org/showthread.php?p=4036966&posted=1#post4036966](http://ubuntuforums.org/showthread.php?p=4036966&posted=1#post4036966)

---

