---
title: "Can't get my DVI to work"
date: 2010-03-27
forum: Apple Hardware Users
---

### Post by Tu1J4kXk8NUhMz on 2010-03-27
I have an adapter which allows my MacbookPro 2,2 to connect to the TV. When I plug it in and open up Monitors, it recognizes there's something there. But when I turn the display on and hit Apply, I get the following message:

The selected configuration for displays could not be applied. Could not find a suitable configuration of screens.

A time or two I've gotten it to not give me the error, but still nothing shows on the TV. Also, I'm not entirely sure how I got this to happen, as it seems a bit sporatic.

Any help would be vastly appreciated. I don't know much about displays on Ubuntu.

Oh, BTW, I'm running Ubuntu 10.04 and Ubuntu Studio 9.10...same problem on both. However, in 10.04 also adds an extra monitor marked "Unknown"...I assume this is some kind of Beta issue.

---

### Post by linuxopjemac on 2010-03-27
```
sudo apt-get install nvidia-settings
nvidia-settings
```

---

### Post by linuxopjemac on 2010-03-27
[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic#Using%20Xinerama](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic#Using%20Xinerama)

---

### Post by Tu1J4kXk8NUhMz on 2010-03-27
My video card is an ATI Radeon x1600. Specs all over the web say its nVidia but I've checked using Ubuntu and OS X, and both tell me I have an ATI Radeon.

---

### Post by linuxopjemac on 2010-03-28
oh, I see, I thought that these models were shipped with nVidia video cards...

Read a bit about the open source radeon driver, it should support dual head.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

dual head:
[http://ubuntu2.wordpress.com/2008/01/02/ubuntu-tip-1-dual-head-on-ati-radeon/](http://ubuntu2.wordpress.com/2008/01/02/ubuntu-tip-1-dual-head-on-ati-radeon/)

Ubuntu page
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

