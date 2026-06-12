---
title: "GUI won't load anymore"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by goltoof on 2007-10-07
I think it all started when I was trying to setup dual desktops for my pc and I played around with my nvidia settings. I restarted xwindows because something wasn't responding by hitting ctrl-alt-backspace and then I just got a blue screen with a ton of errors which all seem to circulate around a "bcm43xx.fw" not being available, then it just goes to a black screen recirculating that error.  Now I can't load my GUI anymore and whenever I restart it just takes me back to that blue screen.

Where do I start? :confused:

---

### Post by -grubby on 2007-10-07
I think it's dpkg (re?)configure xserver-xorg
try it with both the "re" and no re at the beginning of configure

---

### Post by goltoof on 2007-10-07
sudo dpkg-reconfigure xserver-org

i tired that and it looked like it went through but then gave me errors.

---

### Post by bodhi.zazen on 2007-10-07
You can try :

```
sudo nvidia-xconfig
```

And if you have dual monitors :

```
nvidia-xconfig --twinview
```

If that fails, fall back to the vesa driver if you prefer to problem solve in X

---

