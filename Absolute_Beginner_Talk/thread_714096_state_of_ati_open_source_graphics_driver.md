---
title: "state of ati open source graphics driver"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by ub_1234567 on 2008-03-03
Hi,

I have used ubuntu in the past but ended up uninstalling it after finding out that my graphics card (the ati x1400) is not well supported on the operating system. I heard over the news media that ATI has released the specs to allow an open source driver to be developed. I am wondering what is the current state of that driver and if its already stable enough to be used? Can someone point me to a site where they keep the status of this driver?

Thanks!

---

### Post by dstew on 2008-03-03
I think the radeon hd package is the new one based on the released adapter specs. It is available as an Ubuntu package. You can install it with```
sudo apt-get install xserver-xorg-video-radeonhd
```You might have to reconfigure the xserver afterward with```
sudo dpkg-reconfigure xserver-xorg
```and select the radeonhd driver.

---

