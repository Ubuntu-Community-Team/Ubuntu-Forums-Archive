---
title: "what does reconfigure xserver-xorg do?"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by raynard79 on 2007-06-20
Hi forum!

I was trying to get my drivers for my ATI Radeon 9600 going on Ubuntu 7.04, and read in a forum to type in the following command...

         "sudo dpkg-reconfigure xserver-xorg"

Just wondering what this changes, after one does this? 
(ie. what files are modified when you do this...is it just the "xorg.conf" file?

Thanks!!

R.

---

### Post by cogadh on 2007-06-20
It restores your xorg.conf file to a working generic configuration. That's the only file it makes changes to, AFAIK.

---

### Post by overdrank on 2007-06-20
> **raynard79 said:**
> Hi forum!

I was trying to get my drivers for my ATI Radeon 9600 going on Ubuntu 7.04, and read in a forum to type in the following command...

         "sudo dpkg-reconfigure xserver-xorg"

Just wondering what this changes, after one does this? 
(ie. what files are modified when you do this...is it just the "xorg.conf" file?

Thanks!!

R.
HI It will  ie reconfigure your xorg which is basically you graphics, keyboard, and monitor,
You can use a similar command   sudo dpkg-reconfigure -phigh xserver-xorg  this will do it automatically when the other command lets you choose options. Hope this helps:popcorn:

---

### Post by raynard79 on 2007-06-20
Ah, Thanks heaps!!!

I thought I caused more damage than I thought...haha..

thanks.

---

