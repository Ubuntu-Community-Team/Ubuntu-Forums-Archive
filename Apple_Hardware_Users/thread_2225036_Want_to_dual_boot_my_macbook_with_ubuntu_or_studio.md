---
title: "Want to dual boot my macbook with ubuntu or studio ubuntu...."
date: 2014-05-19
forum: Apple Hardware Users
---

### Post by borderblu on 2014-05-19
I've seen the wiki on howto do this by the way, but it seems to be out of date (for instance, a command line suggestion for obtaining info doesn't work on my version of OSX (version 10.9.3), so I wanted to ask people on the forums (hand-holding ;)) what their experiences have been.... Am I going to be able to reinstall OSX if I brick my macbook? I want to record my guitar and use Ardour with my ubuntu installation, will that be possible without latency issues if I go with Ubuntu and not Studio?

My tentative plan is to back up my data, then give the dual boot a shot. I haven't had the macbook long, so it is the latest and greatest hardware:

2.6 I7
16 GB ram
SSD drive

any comments or suggestions would be greated appreciated.

---

### Post by bapoumba on 2014-05-20
*Thread moved to **Apple Users**.*

---

### Post by pixelfairy2 on 2014-05-22
i have the same hardware.

to make usb os x installer, [http://support.apple.com/kb/HT5856](http://support.apple.com/kb/HT5856)
you might want to make a couple just to make sure. 

parallels and vmware fusion both run os x, so you can make a dual boot virtual machine to try this out. on the real hardware, ethernet is the easiest way to get wifi drivers.

one of my backup disks has a bootable lubuntu partition installed from my thinkpad(ubuntu) with kvm. just booted the mac with it and it ran ok, but low res. the ubuntu installer (also usb) had the right res so you should be ok. if you can, try this from an external ssd. you can velcro the enclosure to the lid near the hinge if you want it on the go. 

file vault might screw things up, but it did not stop me from booting to the backup disk or the installer. i also have a boot password but that didnt stop anything either. just used the option key for controlling the boot device, not any external boot manager.

---

