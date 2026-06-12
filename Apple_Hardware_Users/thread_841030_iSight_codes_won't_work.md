---
title: "iSight codes won't work"
date: 2008-06-26
forum: Apple Hardware Users
---

### Post by rakan21 on 2008-06-26
Hello everyone. I have been trying to install my iSight camera to work forever.
I have been taking this tutorial "http://ubuntuforums.org/showthread.php?t=491381"

I have two problems I don't understand when the dude says Change directories to where the tar file is. Then untar it.
Code. Which directory does he mean? /lib/firmware?

and if its on the desktop then when i do Sudo Make i get this error Message:

 sudo make
make -C src
make[1]: Entering directory `/home/rakan/Desktop/against-revision-140/src'
Building USB Video Class driver...
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/rakan/Desktop/against-revision-140/src/uvc_driver.o
/home/rakan/Desktop/against-revision-140/src/uvc_driver.c: In function &#8216;uvc_register_video&#8217;:
/home/rakan/Desktop/against-revision-140/src/uvc_driver.c:1442: error: &#8216;struct video_device&#8217; has no member named &#8216;hardware&#8217;
make[3]: *** [/home/rakan/Desktop/against-revision-140/src/uvc_driver.o] Error 1
make[2]: *** [_module_/home/rakan/Desktop/against-revision-140/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [uvcvideo] Error 2
make[1]: Leaving directory `/home/rakan/Desktop/against-revision-140/src'
make: *** [all] Error 2

I use to get the Error 2 thing when i was installing Wifi but thats working now. I was just wondering on which directory i should extract the folder to and how to fix this error problem. Thanks

Rabayah, Rakan

Oh and if you have a suggestion please send it to [email]rakan21@gmail.com[/email]

Thanks so much

---

### Post by rakan21 on 2008-06-26
anyone ?:(

---

### Post by cyberdork33 on 2008-06-28
that is old. The newest iSights require nothing and should work without issue. Otherwise, you should go here:
[http://ubuntuforums.org/showthread.php?t=764616](http://ubuntuforums.org/showthread.php?t=764616)

---

