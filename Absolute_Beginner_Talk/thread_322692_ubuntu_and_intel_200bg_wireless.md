---
title: "ubuntu and intel 200bg wireless"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by ecosse on 2006-12-20
have installed ubuntu 606 on a hp/compaq nc6220 which has an intel 2200bg wireless module. i can not get the software to see the wireless is even installed. (works find with xp) i have downloaded the ipw2200 drivers but the instructions appear not to work. i can not get make command to accept, just says no command. looking for any help, begining to see msoft as easier option.

---

### Post by jbutler12 on 2006-12-21
You need to use ndiswrapper to "wrap" around the windows driver.  See the following site:

[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

Keep in mind, that to install ndiswrapper-utils, you need to have your ubuntu CD in the drive so it will install off of it instead of looking to the web.  Please post if you run into problems.  You also need to know where your windows driver is (usually you can just use the CD that came with your wireless device), or download it off the internet.

---

### Post by Jussi01 on 2006-12-21
> **jbutler12 said:**
> You need to use ndiswrapper to "wrap" around the windows driver.  See the following site:

[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

Keep in mind, that to install ndiswrapper-utils, you need to have your ubuntu CD in the drive so it will install off of it instead of looking to the web.  Please post if you run into problems.  You also need to know where your windows driver is (usually you can just use the CD that came with your wireless device), or download it off the internet.

There is a native driver for the intel 2200. However it should work out of the box - I have a dell Inspiron laptop with the same card and it worked out of the box. Are you sure the driver is not already installed? have you checked if there is a wireless card enabled in system -> administration -> networking?

EDIT: just noticed you are running dapper - maybe you will need to download the driver as I'm not sure if dapper supports it out of the box.

---

### Post by LookTJ on 2006-12-21
I have exact same card(Intel/PRO 2200BG) that came with my Dell INSPIRON 600m. Works out of the box on both 6.06(Dapper LTS) and 6.10(Edgy)

You sure you connected to your own router? System > Administration > Networking, check the eth1 properties. Make sure it's connected to your router, if it is, Go to next thing which I assume.

What are the DNS nameservers in /etc/resolv.conf? If there are none, set them provided by your ISP. If there are, you're okay with that.

Try disabling [IPv6](http://ubuntuforums.org/showthread.php?t=202838), Still no luck?

Is WEP enabled in the router? If WEP enabled, it will not connect to the internet. 

Make sure Windows isn't messing with DHCP. Still no luck either? Try installing the driver(link provided below)


Try [this](http://packages.debian.org/unstable/net/ipw2200-source)

---

