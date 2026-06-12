---
title: "Nvidia Corporation MCP79 High Definition Audio - Macbook Pro 5,3 - Fedora 13"
date: 2010-06-01
forum: Apple Hardware Users
---

### Post by liquidfunk on 2010-06-01
I also posted this in the Fedora forum.

I've got no sound at all on my Macbook pro after installing Fedora 13. It seems that on Ubuntu 10.04 you have no problems with this generation of MBP, could anyone suggest how I could solve this issue?

Thanks

---

### Post by linuxopjemac on 2010-06-02
For Karmic Koala the trick was to have the alsa backport modules, with a very specific kernel:
[http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=24](http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=24)

I guess you need the latest kernel with the latest alsa module. It should be in kernel 2.6.32
[http://mac.linux.be/content/more-improvements-macs-upcoming-2632-kernel](http://mac.linux.be/content/more-improvements-macs-upcoming-2632-kernel)

Also make sure that all channels are unmuted:
```
alsamixer
```
then unmute with "m"

---

