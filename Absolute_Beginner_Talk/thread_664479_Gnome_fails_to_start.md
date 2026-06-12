---
title: "Gnome fails to start"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Tornam on 2008-01-11
Hello
I am using Ubuntu 7.10 gutsy on an AMD 64.  Problem is my internet connection is crap and it died in the middle of installing updates from the update manager in System >> Administration, so the updates were only partially complete.  When I rebooted my computer I got the following message:

Loading, please wait...
<init: name_to_dev_t(/dev/disk/by_uuid/c2de043a-f588-4517-95db-83b0403d97a5).=hdc5(22,5)
<init: trying to resume from /dev/disk/by_uuid/c2de043a-f588-4517-95db-83b0403d97a5
<init: No resume image, doing normal boot...

Then it went to command line and I could log in, but my internet doesn't seem to work from there (wireless?), and I can't seem to access Gnome.  If I try:

sudo /etc/init.d/gdm start

I get a "Fail".

Anyone have any ideas please?  I'm on my dual boot windows at the moment.  Hope I don't have to reinstall Ubuntu, spent ages downloading drivers etc...

Thanks!

---

### Post by stump138 on 2008-01-11
first thing I would try at the terminal would be
```
startx
```
If x continues to fail you'll need to plug into your network (don't use the wireless) and reboot for simplicity.

Once you are logged back into a terminal with an IP address re-install your desktop
```
sudo apt-get update && sudo aptitude reinstall ubuntu-desktop
```

gl! and post back if that doesn't work for you.

---

