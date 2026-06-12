---
title: "resolution"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by dvanatta on 2007-06-01
I just installed Ubuntu, or any Linux, for the first time.  I notice the screen resolution for my Thinkpad R51 appears to be 800x600 whereas the resolution dialog box say6s it's set for 1024x768, which obviously it isn't.

Do I need special video drivers?  What do I do?

Thanks.

---

### Post by kernel tom on 2007-06-01
yup, drivers are the way to go... 

if u already reconfigured your xorg.conf file, you'll need to know what graphics card you have to get the appropriate drivers

first try to reconfigure your xorg file like this

sudo dpkg-reconfigure xserver-xorg

there will be a section which you can choose supported resolutions... see if by checking off 1024x768 ur problem is fixed

if not... drivers

---

