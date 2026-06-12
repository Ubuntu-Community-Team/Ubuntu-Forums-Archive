---
title: "ndiswrapper alternate driver"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by tartarian on 2007-07-09
I've changed from Ubuntu to Xubuntu and I'm trying to set up my wireless again. I'm going through exactly the same steps that I did when I installed Ubuntu, but I'm getting problems.

When I install the driver for my Ralink FSD7050 from the CD using ndiswrapper, everything installs fine but when I type ndiswrapper -l I get
```

rt2500usb: driver installed
device (050D;7050) present (alternate driver: rt73usb)

```

I never got the 'alternate driver message' on Ubuntu and my wireless won't work no. I had a look on the ndiswrapper homepage and it said consult troubleshooting, but I didn't understand the instructions!
Any ideas what I need to do?
Thanks :)

---

### Post by splintercellguy on 2007-07-09
It's normal, but an indication that you should blacklist the alternate driver so that ndiswrapper can do its job. 

echo 'blacklist rt73usb' | sudo tee -a /etc/modprobe.d/blacklist

After that, reboot.

---

