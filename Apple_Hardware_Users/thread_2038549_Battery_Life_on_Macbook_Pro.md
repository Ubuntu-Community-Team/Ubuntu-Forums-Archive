---
title: "Battery Life on Macbook Pro"
date: 2012-08-06
forum: Apple Hardware Users
---

### Post by chrisduds on 2012-08-06
I'm trying to increase my Macbook's battery life in Ubuntu up from 4 hours using this [thread.]("http://ubuntuforums.org/showthread.php?t=1215928") It says to edit the Xorg.conf file but I couldn't find it and a simple google search reveals that the xorg.conf file is no longer needed since Xorg configures itself. What should I do instead? (I have a Macbook Pro 8,1)

---

### Post by squaregoldfish on 2012-08-07
Xorg.conf is no longer needed, but X will still read it if it's there and override its self-configuration. Simply create it and put in what you need!

Note that it's usually easier to edit a valid xorg.conf file than to write one from scratch. Have a look at Section 6.4.2 on [this page]("http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/x-config.html") that describes how to create one.

Steve.

---

### Post by davidryderuk on 2012-08-07
Hi,
The Macbook Pro 8,1 has an Intel HD 3000 GPU, and the person who wrote that thread you linked to assumes an Nvidia GPU: 

> You probably have some new version of the nvidia driver. 

If your using Intel drivers, then you might want to try these options (which may cause instability):

[http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

---

