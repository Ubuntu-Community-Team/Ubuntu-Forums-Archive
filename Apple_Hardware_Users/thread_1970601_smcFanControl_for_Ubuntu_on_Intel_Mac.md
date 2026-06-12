---
title: "smcFanControl for Ubuntu on Intel Mac?"
date: 2012-05-01
forum: Apple Hardware Users
---

### Post by subehsharma on 2012-05-01
I've installed Ubuntu on my MBP 2012. Mac seems to get pretty hot quickly without any load and so i am searching for a program like smcFanControl that i have on Mac OS X for increasing/decreasing the fan speed. Please let me know if anybody knows about it?

---

### Post by subehsharma on 2012-05-03
Anyone???

---

### Post by Grumpey on 2012-05-03
you can try macfanctrld

Instructions to add the PPA are here: [https://wiki.ubuntu.com/MactelSupportTeam/PPA#Installation](https://wiki.ubuntu.com/MactelSupportTeam/PPA#Installation)

or the PPA is:
[https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=precise](https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=precise)


I've just finished loading 12.04 adn this on a macbook pro 5,1. and it seems to be working using the default config (/etc/macfanctld.conf)

---

### Post by subehsharma on 2012-05-04
Thanks..after installing it, do i need to reboot mac to make it active or it automatically starts running once the installation is completed?

---

### Post by Grumpey on 2012-05-04
It starts after the installation.

---

### Post by candlerb on 2012-05-30
> **subehsharma said:**
> I've installed Ubuntu on my MBP 2012. Mac seems to get pretty hot quickly without any load and so i am searching for a program like smcFanControl that i have on Mac OS X for increasing/decreasing the fan speed. Please let me know if anybody knows about it?

There is a version of smcfancontrol for Linux:

[http://ubuntuforums.org/showthread.php?t=1754431](http://ubuntuforums.org/showthread.php?t=1754431)
[http://ubuntuforums.org/showthread.php?t=1102465](http://ubuntuforums.org/showthread.php?t=1102465)

I had to hack it a bit to work properly on a Macmini4,1

It looks like the "modern" solution is to use macfanctld from Natty PPA, but I have not had a chance to test this yet.

BTW to get your exact model number use this command: dmidecode -s system-product-name

---

