---
title: "iphone 4 unable to mount in ubuntu 11.04"
date: 2011-08-19
forum: Apple Hardware Users
---

### Post by jepperstone on 2011-08-19
Hi!

I have an iPhone 4 (iOS 4.3.5, factory unlocked, not jailbroken) and I wish to use it with Ubuntu 11.04. However, I get the following error when I plug in my iPhone via USB:

> DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

I tried this:
```
sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```
and rebooted. I still get the same error. My goal is to be able to use iFuse (unless there's another program which anyone recommends using for iPhone). If you need more information to help me, let me know.

Thanks for your help!

---

### Post by jepperstone on 2011-09-14
wow. found something that worked! from here: [http://ubuntuforums.org/showthread.php?t=1628529&page=3]("http://ubuntuforums.org/showthread.php?t=1628529&page=3")

> **DodgeV83 said:**
> The PPA by itself didn't work for me.  I then had to run:
```

idevicepair unpair
idevicepair pair
idevicepair validate
```

Got the answer from the following Bug Reports

[http://libiphone.lighthouseapp.com/projects/27916/tickets/183-cannon-mount-iphone-with-ios-421-in-ubuntu-1010#ticket-183-13](http://libiphone.lighthouseapp.com/projects/27916/tickets/183-cannon-mount-iphone-with-ios-421-in-ubuntu-1010#ticket-183-13)

[http://libiphone.lighthouseapp.com/projects/27916/tickets/181-cant-mount-iphone-in-ios-421#ticket-181-10](http://libiphone.lighthouseapp.com/projects/27916/tickets/181-cant-mount-iphone-in-ios-421#ticket-181-10)

---

### Post by Shonnayy on 2011-10-20
How do I upload my iphone calendar into my yahoo calendar on my pc?
My iphone calendar is fully populated with information. My yahoo calendar is [ipad 2 cases](http://www.ebelow.com/ipad-2-case-iPad2case-iPad-2-cases.html) [ipad2 leather cases](http://www.ebelow.com/ipad-2-leather-cases.html) [ipad2 cover](http://www.ebelow.com/ipad-2-covers-leather-ipad-2-covers-ipad2cover.html) blank but I'd like to sync the 2 calendars so I have a back up of my iphone.

---

