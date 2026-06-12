---
title: "video capture shuddery kino- load module?"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by sam_uk on 2006-10-30
I am trying to capture video using kino. I am using this hardware; [http://wirelessimage3.pbwiki.com/f/lshw](http://wirelessimage3.pbwiki.com/f/lshw) running edgy.

I see a shuddery image in the kino caputure window and also in subsequent viewing in cinelerra. The audio captures OK

I have been following the kino tutorial [http://www.robfisher.net/video/kino.html](http://www.robfisher.net/video/kino.html)

i have looked at this article
[http://www.kinodv.org/article/static/3](http://www.kinodv.org/article/static/3)

I have done the modprobing as described here
[http://www.kerklied.com/adrie/presentatiedvdmakeneng.html](http://www.kerklied.com/adrie/presentatiedvdmakeneng.html)

it just returns the command promt so i assume it is working.

Kino says the IEEe 1394 subsystem is not responding.
The raw1394 module must be loaded and you must have r/rw access to /dev/dv1394/0

This is my command line, but i dont understand it; 


~$ lsmod | grep 1394
video1394              20184  0
dv1394                 22104  2
raw1394                30584  0
ohci1394               37040  2 video1394,dv1394
ieee1394              306104  5 video1394,sbp2,dv1394,raw1394,ohci1394
                                  

Í have installed all of these [http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=edgy&release=all&keywords=libdc1394&sourceid=mozilla-search](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=edgy&release=all&keywords=libdc1394&sourceid=mozilla-search)

can anyone help me to load the raw1394 module?

Thanks

Sam

btw i just installed ubuntu yesterday and i love it :)

---

### Post by sam_uk on 2006-10-31
shameless post promotion - no responses yet..

---

### Post by sam_uk on 2006-11-01
might this help?
[http://www.bxlug.be/en/articles/220](http://www.bxlug.be/en/articles/220) the only problem is i have never created a script before.. how do you do it?

---

