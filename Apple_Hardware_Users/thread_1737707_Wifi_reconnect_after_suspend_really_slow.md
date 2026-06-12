---
title: "Wifi reconnect after suspend really slow"
date: 2011-04-23
forum: Apple Hardware Users
---

### Post by cyberco on 2011-04-23
I've been running 10.10 happily on my MacBook Air 3,2 for months now, but the only problem is that reconnecting to Wifi after suspend takes about 30 seconds. That's a lot more than in OSX and something I'm deerly missing. Any suggestions? I have followed this guide for installing 10.10:

[https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat)

---

### Post by mildfuzz on 2012-05-13
I am having the same issue with 12.04 on a Macbook 4.1

---

### Post by cyberco on 2012-05-13
I have been running 12.04 on my MacBook Air 3,2 for a month without any problems whatsoever, but this week the network reconnect started to become slow. So if I open the lid and the Air resumes from sleep it takes about 15 seconds before it starts scanning for wifi connections. Previously with 12.04 the network was found and connected almost instantly. I have no idea which patch changed this behaviour but it is quite annoying. Anybody experienced the same?

---

### Post by poliva on 2012-05-15
> **cyberco said:**
> Anybody experienced the same?

Yes, see this bug:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/994739](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/994739)

Also the following comments:

[http://ubuntuforums.org/showpost.php?p=11912029&postcount=820](http://ubuntuforums.org/showpost.php?p=11912029&postcount=820)
[http://ubuntuforums.org/showpost.php?p=11913371&postcount=821](http://ubuntuforums.org/showpost.php?p=11913371&postcount=821)
[http://ubuntuforums.org/showpost.php?p=11914751&postcount=822](http://ubuntuforums.org/showpost.php?p=11914751&postcount=822)

---

### Post by poliva on 2012-05-17
A quick comment just to let you know a solution is available, see here:

[http://ubuntuforums.org/showthread.php?p=11943846&postcount=844](http://ubuntuforums.org/showthread.php?p=11943846&postcount=844)

---

