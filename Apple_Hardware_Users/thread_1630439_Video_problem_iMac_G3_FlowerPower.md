---
title: "Video problem iMac G3 FlowerPower"
date: 2010-11-25
forum: Apple Hardware Users
---

### Post by joca138 on 2010-11-25
I have one iMac G3 FlowerPower and successfully installed Ubuntu 9.10 on it. Now I have some problems, first is the video, it's works only in 800x600 16 colors, I have looked all around and make severals changes on xorg.conf without success, can someone give me a light for that? Thanks!

---

### Post by linuxopjemac on 2010-11-25
link in everymac.com to your computer please

---

### Post by joca138 on 2010-11-25
> **linuxopjemac said:**
> link in everymac.com to your computer please
This one: [Apple iMac G3/600 SE (Early 2001)]("http://www.everymac.com/systems/apple/imac/stats/imac_se_600.html")

---

### Post by linuxopjemac on 2010-11-25
There is a lot of choice, try this:
```

wget http://mac.linux.be/files/xorg/imac7.txt
sudo mv imac7.txt /etc/X11/xorg.conf
```
reboot and enjoy

---

### Post by joca138 on 2010-11-25
> **linuxopjemac said:**
> There is a lot of choice, try this:
```

wget http://mac.linux.be/files/xorg/imac7.txt
sudo mv imac7.txt /etc/X11/xorg.conf
```
reboot and enjoy
Thanks for helping, but with that configuration I get the message: "no driver" and the gnome don't start... :(

---

### Post by linuxopjemac on 2010-11-25
no driver, weird

sudo apt-get install xserver-xorg-video-ati

---

