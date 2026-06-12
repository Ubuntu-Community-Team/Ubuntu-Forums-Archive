---
title: "Missing Wired Ethernet Connectivity &amp; Graphics Problems"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by borissamaru on 2008-03-27
Hi there,

I have just successfully set up my new laptop (which came with Vista Home Premium) to dual boot. It worked, and I can now boot into either Vista or Ubuntu 7.10. This in its own right was quite an achievement for me.

However, I do have a couple of difficulties in my installed Ubuntu.

My Laptop is a Fujitsu Siemens Esprimo Mobile V5535 Laptop Intel Celeron 530.

a) No Ethernet Connectivity. (This is my current major issue)

The highest priority issue is that I have no Ethernet Connectivity at all. Looking in System => Administration => Networking, there is only a disabled modem connection listed. It appears the install did not detect/install the Ethernet Connection at all. I can't figure out what I need to do to get the system to recognise/detect that I have a wired Ethernet connection.

The Ethernet Hardware is described as an SIS 191 Ethernet Controller.

I am not concerned about wireless; I just want to get the wired connection working.

b) Graphics Not Correctly Set Up (Lower Priority)

I'll deal with this after Ethernet sorted out. Basically Ubuntu does not seem to get on very well with the graphics hardware on this laptop.

In reality the laptop has SIS Mirage 3 Graphics, with an SIS6350 chip and a 1280 x 800 TFT Screen.

By default I'm only getting 800 x 600. (I am not offered any higher resolutions). 
I've tried manually updating settings for Graphics for SIS & a 1280 x 800 LCD, but can't get anything to work beyond the default I have been given by Ubuntu at installation.

If anyone can shine any light on either issue, especially the wired Ethernet not working, it would be greatly appreciated.

Many Thanks,

Boris

[email]borissamaru@yahoo.co.uk[/email]

---

### Post by wolfen69 on 2008-03-27
i would suggest trying the Hardy Heron live cd and see if ethernet works. it may even see your wireless. it has many more drivers than gutsy.  here is the download link. [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)  remember that it is beta, but it works pretty well for me.

---

### Post by OffAxis on 2008-03-27
get to a terminal and type this command

```
ifconfig
```

what does it output?

EDIT: Nevermind. It's listed as non-functional here:
[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsSis](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsSis)

I think your only option is the liveCD above.

---

### Post by borissamaru on 2008-03-27
OK Thanks.

---

### Post by borissamaru on 2008-03-27
I get this from ifconfig :-

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Many Thanks,

Boris

---

### Post by borissamaru on 2008-03-27
> **OffAxis said:**
> get to a terminal and type this command

```
ifconfig
```

what does it output?

EDIT: Nevermind. It's listed as non-functional here:
[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsSis](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsSis)

I think your only option is the liveCD above.

OK, Thanks for your help All.

---

### Post by zvacet on 2008-03-27
[Here #6](http://ubuntuforums.org/showthread.php?t=704585&highlight=pppoe) I hope it will be helpful to you.

---

