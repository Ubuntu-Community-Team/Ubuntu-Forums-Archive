---
title: "Resolution Problem Dell Inspiron 1100"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by boss9192 on 2007-05-16
I just installed the newest version of Ubuntu on my Dell Inspiron 1100.  The resolution is at 640x480 and it won't let me change the resolution to a higher setting.  I am guessing that the proper driver is not installed.

Where can I get this driver online?  I have a drivers disc that came with my laptop, but I would assume it only works for Windows.

---

### Post by bapoumba on 2007-05-16
What video card do you have?

Please run:
```
sudo dpkg-reconfigure xserver-xorg
```
Keep default answers when you do not know.
Select items with <space> (mark a * in the resolutions you want to set for ex).

Restart X with CTRL-ALT-Backspace.

---

### Post by renzokuken on 2007-05-16
you are correct it will only work with with windows.

but fear not, do you know what grafix chipset you have (nvidia, ati, intel ???). i'll show you how to change driver.

---

### Post by veloce on 2007-05-16
> **boss9192 said:**
> I just installed the newest version of Ubuntu on my Dell Inspiron 1100.  The resolution is at 640x480 and it won't let me change the resolution to a higher setting.  I am guessing that the proper driver is not installed.

Where can I get this driver online?  I have a drivers disc that came with my laptop, but I would assume it only works for Windows.

Checkout:

[https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

---

### Post by boss9192 on 2007-05-17
Here are the specs for the computer:

[http://reviews.cnet.com/laptops/dell-inspiron-1100/4507-3121_7-21127907.html?tag=sub](http://reviews.cnet.com/laptops/dell-inspiron-1100/4507-3121_7-21127907.html?tag=sub)

---

### Post by veloce on 2007-05-17
> **boss9192 said:**
> Here are the specs for the computer:

[http://reviews.cnet.com/laptops/dell-inspiron-1100/4507-3121_7-21127907.html?tag=sub](http://reviews.cnet.com/laptops/dell-inspiron-1100/4507-3121_7-21127907.html?tag=sub)

So it is definately an intel graphics chipset.  As mentioned in the article I referred to, the intel graphics bios does not register all modes and needs the 915resolution software to run properly.

Step 1: use synaptic package manager to install 915resolution.

This may solve all your problems!

---

### Post by pigboy306 on 2007-05-17
Can you help with an Acer Travelmate with ATI 9100 chipset. I can not select my correct resoloution

---

### Post by renzokuken on 2007-05-17
could you post your xorg.conf pigboy306

/etc/X11/xorg.conf

---

