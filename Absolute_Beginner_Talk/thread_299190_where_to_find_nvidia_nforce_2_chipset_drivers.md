---
title: "where to find nvidia nforce 2 chipset drivers?"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by billybobjoe on 2006-11-13
I have an old Biostar m7ncg 400 amd socket a motherboard.  I have searched high and low for Linux (Ubuntu) drivers for this board which has a nvidia nforce 2 chipset.  I have just installed the newest version of Ubuntu and have never ran Linux before, so I wanted to find out what it was all about.  I am mainly looking for the graphics drivers, because the bad resolution is giving me a headache, and i need a sound driver.  Any help will do.  THANKS.

My system is:
Biostar m7ncg 400 version 7.2
AMD socket 'A' 2000+ overclocked to just over 2.1 GHZ on air!
integrated video
integrated audio

---

### Post by b_martinez on 2006-11-13
You need the legacy drivers for a card that old.  Read this, it may help you out.

[http://www.ubuntuforums.org/showthread.php?t=299141]("http://www.ubuntuforums.org/showthread.php?t=299141")

There are also other links in this one. Follow them and you may find out exactly which driver(s) you need.
hth
Bill

---

### Post by ReaderRat on 2006-11-13
nVIDIA linux drivers?
**[http://www.nvidia.com/object/linux_nforce_1.0-0261](http://www.nvidia.com/object/linux_nforce_1.0-0261)**
EDIT:Looks like all these are for different distros...don't know if they will work, sorry. they do have an .rpm file for Red Hat, but it would need to be converted to a .deb file.

---

### Post by ReaderRat on 2006-11-13
I checked the mobo specs and it runs AC'97 audio. Here are a couple of things to try...
**[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)**
[**AC'97 ICH6 Audio**](http://ubuntuforums.org/showpost.php?p=1733758&postcount=3)

---

### Post by billybobjoe on 2006-11-14
Thanks for the help guys, ill try them this weekend.

---

