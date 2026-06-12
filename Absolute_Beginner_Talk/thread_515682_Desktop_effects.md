---
title: "Desktop effects"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Dark_X on 2007-08-02
When I enable desktop effects I get this error message.
[IMG]http://i201.photobucket.com/albums/aa145/Dark_X1079/Screenshot-1.png[/IMG]
I have a Radeon Xpress 200 series.

---

### Post by Raineer on 2007-08-02
You will need to have a 3d-accelerated driver enabled for Desktop Effects to run.  For ATI this is a bit more difficult than with an NVidia card, I would recommend heading over to the Desktop Effects & Customization" forum and do some searching.

---

### Post by w4ett on 2007-08-02
You will have to enable the Restricted Driver for you video card, or use the Envy Installation Application to install the Driver.

[http://www.albertomilone.com](http://www.albertomilone.com)

Alternatively you can try to use the native driver 'ati' already in xorg  (this is the one I'm using).

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and select ati as your driver.

---

