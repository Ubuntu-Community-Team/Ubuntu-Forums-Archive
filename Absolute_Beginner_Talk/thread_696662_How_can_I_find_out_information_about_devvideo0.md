---
title: "How can I find out information about /dev/video0"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-02-14
/dev/video0 is my webcam...

But what if I had a TV Tuner card also installed?

How would I know which is which?

How do you find out information about the devices?  What's the proper way?

---

### Post by Cypher on 2008-02-14
The naming of the various devices is handled by the drivers that manage those devices. So if you do something like
```

dmesg | grep -i eth

```
You will find that during your system bootup, the Kernel using the Ethernet driver found your Ethernet card and assigned it a device name starting wtih 0 for each device that was found. WiFi drivers like to use the "wlan" prefix..and so on.

So if you had a TV Tuner installed, you'd need some sort of a driver for that device, that documentation for said driver would indicate what their preferred naming would be and in turn you could do the above command but replace the "eth" with whatever the TV Tuner driver says they use..

The files in the /dev directory are conduits of access to a particular driver. What is more important than the name is the Major and Minor number that goes with each of these devices. So the name is truely arbirtrary, you could easily called your Ethernet adapter "JohnSmith0" with the correct major and minor numbers and with the name changed everywhere else, it would work..

---

### Post by badmedic on 2008-02-14
You can also look through "System > Preferences > Hardware Information". The advanced tab for each device lists most of the technical information, including the device file which includes the name. 

For example, my laptop has a built in camera that lists "linux.device_file" as "/dev/video0"

---

