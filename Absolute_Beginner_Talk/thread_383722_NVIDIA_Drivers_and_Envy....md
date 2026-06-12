---
title: "NVIDIA Drivers and Envy..."
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by morari on 2007-03-13
Though I'm actually using Kubuntu, their forums seem to be down at the moment though. I didn't figure the methods would differ too much (if at all, really).

After a lot of struggling with my video card, and a reinstall of the entire OS even, I came across Envy. I'm led to believe that it's a fairly automated process with a nice graphical interface? Anyway, I downloaded the package but when I attempt to install it I receive the following error:

```
tar: ./md5sums: Cannot utime: Bad file descriptor
tar: ./control: Cannot utime: Bad fil descriptor
tar: .: Cannot utime: Bad file descriptor
tar: Error exit delayed from previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /home/alexander/desktop/envy_0.9.1-0ubuntu3_stall):
  subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
  /home/alexander/Desktop/envy_0.9.1-oubuntu3_all.deb
Press <enter> to exit...
```

So... Yeah. Needless to say, I'm kind of confused at this point and would very much appreciate a bit of advice. :confused: :confused: :confused:

---

### Post by Mohammad_Khalid_Hussain on 2007-03-13
Yeah it is suppose to be what it is. But trying to get it installed is not easy. Especially for new people just as I who has used it for only 2 days. Downloaded it and everything but then I was stuck, I didnt know how to get it running.

Anyway since I also have an Nvidia card(Nvidia 5500 FX), I just followed his manual guide:
[http://www.albertomilone.com/latest_nvidia_udsf_edgy.html](http://www.albertomilone.com/latest_nvidia_udsf_edgy.html)

This is for Edgy Eft and if followed carefully will get to install Nvidia's proprietary drivers.

Note: Internet access is required as the driver needs to be downloaded and is not small in size.

Hope you can get it fixed.

---

### Post by lilchris173 on 2007-03-13
You can also use EasyUbuntu or Automatix. Automatix would probably be your best bet because its so heavily used. [www.getautomatix.com](www.getautomatix.com) . Installation is a BREEZZEEE for anyone... You can also get all the programs you'd normally want on a fresh installation. Good luck. If you need more help go to [www.theneosa.org](www.theneosa.org) if you wish.

---

### Post by Aliarse on 2007-03-13
Another vote for automatix. 

I too tried the envy script when i first ever used ubuntu, and while it did install, it broke the xserver, and as a newb i didnt know how to fix it (i now do), so i installed automatix which worked first time!

---

