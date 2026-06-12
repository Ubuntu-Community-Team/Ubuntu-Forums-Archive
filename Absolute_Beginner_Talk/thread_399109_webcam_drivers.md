---
title: "webcam drivers"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by nwadams on 2007-04-01
i need help installing this plz:   
Microdia Triplex i-mini PC Camera

that's what lsusb gave me

---

### Post by FakeOutdoorsman on 2007-04-01
I bet this is a Sonix chipset web cam.  Unfortunately the manufacturer doesn't supply drivers for this.  Fortunately there is an open source alternative: [Sonix SN9C102 based webcam driver]("http://sonix.sourceforge.net/").

You may also be interested in the [sn-webcam project]("http://sn-webcam.sourceforge.net/").

---

### Post by nwadams on 2007-04-01
thanks a lot, i'll see how this goes

---

### Post by djamu on 2007-04-02
Just for your info

I have Sweex Mini Webcam ( about the cheapest cam you can buy ), which isn't supposed be to be supported by Linux.... ( no driver support by Sweex )

Well guess what, installing camorama, just made it work without installing & compiling any additional drivers....:lolflag: 
seems that the SN9C102 driver is already built in

```
root@ubuntu:/# lsusb
Bus 004 Device 003: ID 059f:0651 LaCie, Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 013: ID 0c45:6005 Microdia Sweex Mini WebCam
Bus 002 Device 001: ID 0000:0000 

```
```

root@ubuntu:/# caminfo 
Detected 1 Video4Linux devices.
Device node      : /dev/video0
Name of device   : "Sweex SIF webcam"
Minimum size     : 160x120
Current size     : 0x0
Maximum size     : 352x288
Video inputs     : 1
 Input 0
  Name             : "SN9C102"
  Type             : Camera
  Audio            : no
  Tuners           : 0
Audio inputs     : 0

```

I did an Install of ZoneMinder , but I doubt if this would have solved any issues

Jan

---

### Post by nwadams on 2007-12-02
'im bumping and old topic here, but i still can't get it to work with the advice given, i ahve no idea exactly what to do...lol,

---

### Post by gupta_sumesh63 on 2007-12-02
Well, You can try the following site. It gives all the drivers for all types of webcams.
> [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)
Hope this helps.

---

### Post by nwadams on 2007-12-02
ok, i'm a newb, how do i install it after I downladed it

---

### Post by gupta_sumesh63 on 2007-12-02
See this post. It should help you install the drivers.

> [http://ubuntuforums.org/showthread.php?t=425801](http://ubuntuforums.org/showthread.php?t=425801)

and this
> [http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

It would have been better if you had downloaded the .deb version.

---

### Post by metalpancake on 2007-12-02
Canorama from add/remove applications seems to work with most webcams.

---

### Post by grinias on 2008-01-11
What follows, refers to "Microdia Sweex Mini WebCam" (taken by lsusb), but i think that it will work for you.
The problem has to do with the order that gspca and sn9c102 drivers are loaded.
If you do 

```

sudo modprobe -r sn9c102
sudo modprobe -r gspca

```

and then
```

sudo modprobe  gspca

```

the webcam will function perfectly.

---

### Post by vivalant on 2008-01-11
Or try the driver at SN9CXXX at [http://www.linux-projects.org](http://www.linux-projects.org) , which is fairly better

---

### Post by grinias on 2008-01-13
> **vivalant said:**
> Or try the driver at SN9CXXX at [http://www.linux-projects.org](http://www.linux-projects.org) , which is fairly better

For skype it did not work. I used the trial version of the driver you suggest for gutsy. caminfo and camorama recognized the camera successfully thought.

---

### Post by vivalant on 2008-01-13
In the FAQ the authout says that skype does not work bacause Skype does not support the formats exported by the driver. So it's a skypes fault for now. Let's hope the following beta will fix this.

---

### Post by grinias on 2008-01-13
> **vivalant said:**
> In the FAQ the authout says that skype does not work bacause Skype does not support the formats exported by the driver. So it's a skypes fault for now. Let's hope the following beta will fix this.

Indeed, skype video is beta. What about the "trial" state of driver for gutsy? Is it permanent? And what happens after the trial period?

Anyway, thanx for the driver link info.

---

### Post by vivalant on 2008-01-13
> **grinias said:**
> Indeed, skype video is beta. What about the "trial" state of driver for gutsy? Is it permanent? And what happens after the trial period?


It will happen that your driver is no longer working..
 
I think you will have to pay for the unlimited version, as mentioned here:
[http://www.linux-projects.org/downloads/sn9cxxx-unlimited.html](http://www.linux-projects.org/downloads/sn9cxxx-unlimited.html)

or here (question 4 of the FAQ)
[http://www.linux-projects.org/downloads/FAQ.html](http://www.linux-projects.org/downloads/FAQ.html)

---

### Post by grinias on 2008-01-14
ok, thanx again...although I do not like the idea of paying for software...

---

