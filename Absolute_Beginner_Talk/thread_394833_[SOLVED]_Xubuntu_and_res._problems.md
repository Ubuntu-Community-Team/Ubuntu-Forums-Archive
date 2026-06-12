---
title: "[SOLVED] Xubuntu and res. problems"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by dougleduck on 2007-03-27
I'm brand new to Xubuntu today...and my problem is that my screen resolution is only 600x480. When i go to display settings i dont get any choice for what resolution.

I've read a few different things and I can't quite fathom how to do it, and ive checked the xorg.config file and the correct res. (1080x768) is listed under the possible resolutions. 

Can anyone give me a step by step guide on possible ways to change it, or point me to somewhere that gives simple guide?

my graphics processor is Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device,

Ive also attached .txt version of xorg.conf

---

### Post by dstew on 2007-03-27
The open-source driver i810 was installed by default, and it may not be able to do any better. If you want to get more resolution and better performance, you may need to install the proprietary linux driver for your graphics card. This is not easy, but can be done if you want to.

[http://www.intellinuxgraphics.org/](http://www.intellinuxgraphics.org/)

EDIT: According to the website, the driver name i810 has been deprecated, and the new name is intel. You can try to edit your xorg.conf file, and change i810 to intel, and see if that helps.

---

### Post by dougleduck on 2007-03-27
thanks,

I found an easier way to fix it though.

copy the following page into xorg.conf. Worked straight away then...just in case anyone else has this problem.

[http://www.geocities.com/randomnumbergenerator2001/xorg.conf.breezy.txt](http://www.geocities.com/randomnumbergenerator2001/xorg.conf.breezy.txt)

---

