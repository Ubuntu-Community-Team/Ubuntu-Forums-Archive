---
title: "[SOLVED] Brightness, coulor control etc..?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by MangasColoradas on 2007-12-24
I am using the restricted ATI driver and was wondering if there is a way to control brightness etc,.

I installed fglrx-control from synaptic but cant get it working with what I think is the symlink, cant see it anywhere else.

Also, I tried 'xgamma' in the terminal and got this...

[I]Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
Unable to query video extension version
[/I]

---

### Post by zhouxing on 2007-12-24
Install latest ATI Catalyst Control from [www.ati.com](www.ati.com), then you will be able to do it.

---

### Post by MangasColoradas on 2007-12-24
Thanks, I found this but it looks like its the driver and not just catalyst control centre.

[http://ati.amd.com/support/drivers/linux/previous/linux-r-cat711.html](http://ati.amd.com/support/drivers/linux/previous/linux-r-cat711.html)

---

### Post by MangasColoradas on 2007-12-24
Its a shame xgamma wont work.

---

### Post by zhouxing on 2007-12-24
What exactly is your ATI card? Mine is X300. There is a latest driver issued by ATI in December 2007. Your link is the one issued in November 2007.

After installation of this driver, you will have catalyst in your Application.

---

### Post by MangasColoradas on 2007-12-24
I am using the restricted driver now, which I think is Novembers?

I just wanted the catalyst cc as a seperate thing but I *could* install it from the ATI website and get the catalyst that way.

I have a 9800pro BTW.

---

### Post by zhouxing on 2007-12-24
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-7-12-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-7-12-x86.x86_64.run)

Download from this link for the latest ati catalyst 7.12

---

### Post by blueridgedog on 2007-12-24
Will the driver on the ATI site work with xserver-xgl?  I see they comment that it is for X.Org.

---

### Post by MangasColoradas on 2007-12-24
No the latest doesnt use xgl it uses AIGLX, I cant use the latest driver with my card.

I could try to follow quite an advanced tutorial to do it but last time I did that I screwed everything up.

Thats why I linked to the older one.

---

### Post by MangasColoradas on 2007-12-25
Well I followed that tutorial and now Compiz wont work. The new driver is installed and glxinfo and fgrlx info are all correct.

xgamma works tho! LOL!

Oh yea and the graphics are still not right, I get a black line around minimising windows.

---

