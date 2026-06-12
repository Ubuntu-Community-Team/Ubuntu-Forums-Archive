---
title: "iMac DV, Debian 5.03, Webcam Vista Plus"
date: 2010-03-08
forum: Apple Hardware Users
---

### Post by noriek on 2010-03-08
Hi All,

I have the cheapo "Creative Webcam Vista Plus" which I have previously had working with Xubuntu 8.10 on the i386 architecture, 'tho I have no recollection as to how I got it to work. Any knowledge/indication as to whether or not it is supported by the PPC arch. If so, can somebody please walk me through the process or point me to the appropriate page (which I can't seem to find)?

Thanks

---

### Post by linuxopjemac on 2010-03-08
According to [this website]("http://opensource.creative.com/webcam.html"), you have to go [here]("http://mxhaard.free.fr/download.html").

You have to compile the tarball yourself I guess.

You can try to see if it is a module in the kernel

```
sudo modprobe gspca
```
or
```
sudo modprobe gspcav1
```

also interesting here:
[http://blog.myfenris.net/?p=377](http://blog.myfenris.net/?p=377)
[http://www.linuxjournal.com/video/get-your-webcam-working-gspca](http://www.linuxjournal.com/video/get-your-webcam-working-gspca)

google yourself a bit with gspca

---

