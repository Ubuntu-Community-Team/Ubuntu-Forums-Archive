---
title: "spca5xx"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by Bruce2 on 2007-12-29
How do I get this installed on my computer?

I went to a site and downloaded the latest version of this, but got a screen on my computer that said location/....... I dont know what to do with it.

Also I am running Ubuntu 7.04. Does this already have spca5xx?

Thankyou.

---

### Post by RomeReactor on 2007-12-29
Hi. You can install the **spca5xx-source** package from Synaptic; you need the Universe repository enabled. This is the source code from where you can then build the driver.

EDIT: You also need the headers for your current kernel; to install them and the driver from the terminal:
```
sudo apt-get install spca5xx-source linux-headers-`uname -r`
```

---

### Post by loell on 2007-12-29
spca5xx driver/module for webcam is already installed in ubuntu by default , if you have a webcam that is spca5xx compatible, then its just plug and play.

---

### Post by Bruce2 on 2007-12-29
loell, I have tried to plug it in and play it, but its not working. Maybe its just not compatible.

Are there any webcams out there that are proven to just plug straight in to a linux computer and run without installing anything?

Romereactor, what is Synaptic?

---

### Post by loell on 2007-12-29
by far the only profound list of webcams are in 

[http://mxhaard.free.fr/spca5xx.html]("http://mxhaard.free.fr/spca5xx.html")

when the table states "yes" then its more likely to be plug and play. 

some additional reference ,  [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)


most logitech webcams are found to be compatible with spca5xx and/or in Ubuntu.

---

### Post by RomeReactor on 2007-12-29
Bruce, Synaptic is the package manager in Ubuntu, located in "System-Administration->Synaptic"; the terminal is located in "Applications->Accessories->Terminal". If you're using Kubuntu, then look for the packages in Adept, or use Konsole to run the commands.

You'll also need to install another package which you may not have, so to install everything needed:
```
sudo apt-get install spca5xx-source linux-headers-`uname -r` module-assistant
```

Once the packages are installed, you can read the instructions like this:
```
cat /usr/share/doc/spca5xx-source/README.Debian
```

---

