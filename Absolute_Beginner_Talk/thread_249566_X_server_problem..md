---
title: "X server problem."
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Ghozt on 2006-09-02
No, it has nothing to do with the update.

I've been happily running ubuntu on my laptop for a few weeks now, and I'm ready to install it on my desktop. I've come across some errors.

When I try to run the LiveCD, the boot process looks like it's going fine, but then this happens.

[http://img71.imageshack.us/img71/3955/img6449bv1.jpg](http://img71.imageshack.us/img71/3955/img6449bv1.jpg)
[http://img234.imageshack.us/img234/634/img6450st8.jpg](http://img234.imageshack.us/img234/634/img6450st8.jpg)
[http://img381.imageshack.us/img381/3886/img6451ne5.jpg](http://img381.imageshack.us/img381/3886/img6451ne5.jpg)

It's either a monitor or gfx card problem I'm sure, I just don't know what I should do about it. Do I just need to wait until the new version comes out, or somehow burn a cd with X 7.1 instead of 7.0 (if that's even possible?) I have an ATI Radeon Saphire X850XT PCI-E, and I'm not sure what type of monitor I have (19" LCD MGL something or other, I can check later.) I'm not at home right now, I'm at my buddies giving him his camera back, and writing this real quick.

If you need any other info, just ask. Thanks in advance. :)

---

### Post by taurus on 2006-09-02
Looks to me like the installer is crapping out about your graphic card.  So if you want to install Dapper on your machine, I think you should use the alternate CD since it comes with a text base installer.  Do your normal installation and see if it can configure your video card for you.  If not, you can still configure it after you have finished installing it with

```
sudo dpkg-reconfigure xserver-xorg
```

---

