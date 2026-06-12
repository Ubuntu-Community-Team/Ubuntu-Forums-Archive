---
title: "Mustek Scanner on Ubuntu..."
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by sparkling_twinkle on 2005-10-23
i have my scanner that i have been using when i was still with ms.. could u help me how to install Mustek scanner  600 cp (if possible) to linux.. Thank's a lot!

---

### Post by claydoh on 2005-10-23
First, make sure you have the packages libsane, and xsane installed (you should already have these)

Then go to the Sane Mustek Parallel Port scanner page and follow the directions in the Install section. As we have already checked that we have sane bits installed, the first step is already complete.

You will need to use sudo to edit the dll.conf and mustek_pp.conf

```
sudo gedit </full/path/to/filename>
```

I do not have a Mustek Parallel port scanner so I cannot personally say if/how well it will work. My mustek scanner is a cheap usb model that works fine. I got rid of my Mustek 1200 Parallel port scanner before it was supported in Sane.

---

### Post by alienexplorers on 2007-02-06
Adding libsane-extras provides more backends which you may need.

---

